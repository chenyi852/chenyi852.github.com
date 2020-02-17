layout: post
title: "运用trust zone来保证系统的安全"
subtitle: 'teeos的应用'
author: "Johnny"
header-style: text
tags:

  - Trust zone
  - TeeOS

我们在扫二维码时，很有可能后台运行着恶意程序， 将二维码偷偷地替换掉。这时我们可以在二维码中加入GPS信息，防止二维码被恶意篡改。因为黑客一般都是远程攻击，如果他要只能利用微信来生成二维码，因为微信是比较难被完全攻破的。因此本地生成的二维码中包含的是黑客的真正的GPS地址。这样岂不是等着被警察抓吗？

黑客也不是傻子，当然篡改本地的GPS数据，这样生成的二维码中包含的就是被攻破的手机的GPS数据，这样微信在检测二维码时判断对方的GPS数据离我很近，就认为是合法的（因为扫一扫时，二者的GPS数据很接近）。

但是道高一尺，魔高一丈。我们可以让Trust Zone访问GPS,Android侧是访问不了GPS数据的，这样黑客就无法篡改GPS数据了。自然利用微信生成的二维码中包含的就只能自己真实的数据。
