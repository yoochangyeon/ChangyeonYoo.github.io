---
title:  "MobaXterm 사용하여 EC2 접속하기"
excerpt: "MobaXterm을 이용한 EC2 접속"

categories:
  - WEB
tags:
  - WEB
  - AWS
---

윈도우에서 AWS EC2 서버에 접속하기 위해서 MobaXterm을 사용하였다.

다운로드는 공식 홈페이지([https://mobaxterm.mobatek.net/](https://mobaxterm.mobatek.net/))에서 받을 수 있다.

#### 먼저 AWS EC2에서 포트를 바꿔주어야 한다.

[##_Image|kage@czHOWr/btq2bKJvSiP/JAm38ktDugl2ljzl1KfKbk/img.png|alignLeft|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|||_##]

#### 아래 바를 오른쪽으로 옮기면 보안 그룹이 나오는데, 보안그룹을 클릭해준다.

[##_Image|kage@zXdUc/btq2bJjqxpJ/x0Ti81kuCemPL5We3SlK6k/img.png|widthContent|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|||_##]

#### 이후 인바운드 규칙 - 인바운드 규칙 편집 클릭

[##_Image|kage@ewZd6X/btq2gLfrhA5/pb50skZVkGNIAKqh2pbIm1/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|||_##]

#### 규칙 추가를 눌러주고 포트는 8080, 소스는 0.0.0.0/0 으로 선택해준다. 이후 규칙 저장.

#### MobaXterm을 실행시켜준다.

[##_Image|kage@waPQ2/btq2gJ2ZvJy/dNX17v6s9AKUM8rX1qPRL0/img.png|alignLeft|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|||_##]

#### MobaXterm 실행 후 Session 버튼 클릭

[##_Image|kage@u16dS/btq2dIDWpM0/xk99ejrB394WGnkVFZDRm1/img.png|alignLeft|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|||_##]

#### 이후 SSH 클릭

[##_Image|kage@bk4O3u/btq2c2igwrN/BpLdr9XxigQH3FlkiHsHX0/img.png|alignLeft|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|||_##]

#### Remote host에는 AWS EC2 인스턴스에 있는퍼블릭 DNS(IPv4) 주소를 입력

[##_Image|kage@c1kA60/btq2eLmWWPc/h0YvOQKhAeeIRMD2BNBH61/img.png|alignLeft|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|||_##]

#### 이후 아래에 Advanced SSH settings 탭에 User private key를 체크해주고, 이전에 다운받았던 키 페어를 찾아 클릭해준다.

[##_Image|kage@bhzxxo/btq2gfg0rK8/fm97I2wfwbKcZlj7ptxIBk/img.png|alignLeft|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|||_##]

#### login as에 ubuntu를 입력해주었다.

[##_Image|kage@yp3Vm/btq2dA65PGD/07jmQFlG31Z3bF7gUevBH1/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|||_##]

#### 위에 화면처럼 mobaXterm을 이용하여 AWS EC2 서버에 접속한것을 확인할 수 있다,