SickZil-Machine
===============
<sup>English | [한국어](#식질머신)</sup>

![szmc-0.1.0](doc/szmc-0.1.0.gif)
<sup>(source: [manga109](http://www.manga109.org), © Kanno Hiroshi, © Okuda Momoko, © Kato Masaki)</sup>

SickZil-Machine **automates texts removal** during manga/comics translation(Scanlation) process.
</br></br>
  
![SeisinkiVulnus_028](doc/1.jpg)

![LoveHina_vol14_003](doc/2.jpg)

![AkkeraKanjinchou_031](doc/3.jpg)
All of the above images were edited automatically without human intervention.\
<sup>(source: [manga109](http://www.manga109.org), © Shimazaki Yuzuru, © Akamatsu Ken, © Kobayashi Yuki)</sup>

How it works??
-----
### Model
![szmc-structure-eng](doc/szmc-structure-eng.png)

SickZil-Machine finds out the texts in manga/comics and erases it naturally to match the background.\
**Both processes are completely automatic**, without any additional human intervention.\
Of course, if you want, you can also specify text area you want to erase.

<sub>By the way, SickZil is korean word 식질, slang of 식자(작업).
식자 means editing manga/comics according to the translation(from translator).</sub>

We applied [U-net](https://arxiv.org/abs/1505.04597) for SegNet and [Deepfill v2](http://jiahuiyu.com/deepfill2/) for ComplNet.

### Data set
SickZil-Machine consists of two deep learning models, SegNet and ComplNet.

To learn **SegNet**, we need **original manga images** and \
**text component masks** that cover all text area corresponding to the original images.

To learn **ComplNet**, we need **manga images with text removed** (ie **output**). \
(I'm researching how an images with a small amount of text affects performance. \
 manga images with no text at all are the ideal data.) 

Version 0.1.1 was trained using 285 image-mask pairs and 31,497 manga images. \
(11,464 of 31,497 manga images are images with text.)

If you'd like to contribute a dataset to SickZil-Machine, please send your data to <a href="mailto:kur.creative.org@gmail.com"> email </a>. \
The dataset will only be used for research purposes.

Release
-----
**We released 0.1.1 pre-release version!** \
[You can download SZMC here](https://github.com/KUR-creative/SickZil-Machine/releases). \
[Tutorials and Tips here.](https://github.com/KUR-creative/SickZil-Machine/blob/master/doc/tips/tips-0.1.1-eng.md)

SickZil-Machine is not a perfect program. We need your help. \
If you find a bug or have a suggestion, please open a [Github issue](https://github.com/KUR-creative/SickZil-Machine/issues) or send us an <a href="mailto:kur.creative.org@gmail.com">email</a>.

Run the code(for developers)
----

You need NVIDIA driver 410.x, CUDA 10.0, CUDNN (>= 7.4.1). (tensorflow 1.13.0 requirements)

0. `git clone https://github.com/KUR-creative/SickZil-Machine.git; cd SickZil-Machine`
1. Download one of release zip files from [here](https://github.com/KUR-creative/SickZil-Machine/releases).
2. Unzip the release file and copy `SickZil-Machine-0.1.1-pre0-win64-cpu-eng/resource/cnet` and `SickZil-Machine-0.1.1-pre0-win64-cpu-eng/resource/snet` directories to `SickZil-Machine/resource`.
3. `pip install -r requirements.txt`
4. `cd src; python main.py`

Future works
-----
- Increase text segmentation performance
- Open manga text segmentation mask dataset
- Automate typesetting(calligraphy style learning)

</br>
</br>
</br>

식질머신
========
<sup>[English](#SickZil-Machine) | 한국어</sup>

![szmc-0.1.0](doc/szmc-0.1.0.gif)
<sup>(출처: [manga109](http://www.manga109.org), © Kanno Hiroshi, © Okuda Momoko, © Kato Masaki)</sup>

식질머신은 식자 작업에서 **글자 제거 작업**을 **자동화**합니다.
</br></br>

![SeisinkiVulnus_028](doc/1.jpg)

![LoveHina_vol14_003](doc/2.jpg)

![AkkeraKanjinchou_031](doc/3.jpg)
위 이미지들은 모두 사람의 개입 없이 자동으로 편집되었습니다.\
<sup>(출처: [manga109](http://www.manga109.org), © Shimazaki Yuzuru, © Akamatsu Ken, © Kobayashi Yuki)</sup>

~어케했누
-----

### 모델

![szmc-structure-kor](doc/szmc-structure-kor.png)

식질머신은 만화에서 텍스트를 찾아내고, 자연스럽게 지워냅니다.\
두 과정 모두 사람의 개입 없이 **완전히 자동으로 진행**됩니다.\
물론 원한다면 지우고 싶은 영역을 지정할 수도 있습니다.

SegNet으로 [U-net](https://arxiv.org/abs/1505.04597)을 적용했고, ComplNet으로 [Deepfill v2](http://jiahuiyu.com/deepfill2/)를 적용했습니다.

### 데이터셋
식질머신은 SegNet과 ComplNet 두개의 딥러닝 모델로 이루어집니다. 

**SegNet** 학습을 위해서는 **원본 만화 이미지**와 \
원본에 대응하여 텍스트,효과음 영역을 가리키는 **텍스트 컴포넌트 마스크**가 필요합니다. 

**ComplNet** 학습을 위해서는 **텍스트가 제거된 만화 이미지**(즉, **출력**)가 필요합니다. \
(텍스트가 약간 존재하는 이미지가 성능에 얼마나 영향을 미치는지는 연구 중입니다. \
 텍스트가 전혀 존재하지 않는 만화 이미지가 가장 이상적인 데이터이긴 합니다.)
 
0.1.1 버전은 이미지-마스크 285 쌍과 31,497개의 만화 이미지를 이용하여 학습하였습니다. \
(31,497개의 만화 이미지 중 11,464개는 텍스트가 존재하는 이미지입니다.)
 
식질머신에 데이터셋을 기여하고 싶으시다면 <a href="mailto:kur.creative.org@gmail.com">이메일</a>로 데이터를 보내주시면 됩니다. \
데이터셋은 오직 연구 목적으로만 이용될 것입니다.


Release
-----
**현재 0.1.1 pre-release 버전을 배포하고 있습니다!** \
[여기서 다운로드할 수 있습니다.](https://github.com/KUR-creative/SickZil-Machine/releases) \
[사용방법과 팁](https://github.com/KUR-creative/SickZil-Machine/blob/master/doc/tips/tips-0.1.1-kor.md)

현재 식질머신은 완벽하지 않습니다. 사용자 여러분의 도움이 필요합니다. \
혹시 버그를 발견하셨거나 제안이 있으시다면 [깃헙 이슈](https://github.com/KUR-creative/SickZil-Machine/issues)를 열어 제보해 주시거나 <a href="mailto:kur.creative.org@gmail.com">이메일</a>을 보내주세요.\
특히 이슈의 경우, 영어를 모르시면 그냥 한국어로 쓰셔도 됩니다.    

Run the code(for developers)
----

NVIDIA driver 410.x, CUDA 10.0, CUDNN (>= 7.4.1)이 필요합니다(텐서플로우 1.13.0 요구사항).

0. `git clone https://github.com/KUR-creative/SickZil-Machine.git; cd SickZil-Machine`
1. [여기](https://github.com/KUR-creative/SickZil-Machine/releases)서 릴리즈 빌드 중 하나를 다운로드합니다.
2. 압축을 풀고 `SickZil-Machine-0.1.1-pre0-win64-cpu-eng/resource/cnet` 과 `SickZil-Machine-0.1.1-pre0-win64-cpu-eng/resource/snet` 폴더를 `SickZil-Machine/resource`폴더로 복사합니다.
3. `pip install -r requirements.txt`
4. `cd src; python main.py`

Future works
-----
- 만화 텍스트 세그멘테이션 성능 높이기
- 만화 텍스트 세그멘테이션 마스크 데이터셋 공개하기
- "식자" 자동화하기(손글씨 스타일 학습)
