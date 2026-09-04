# blog-sns-images

SNS(인스타그램·쓰레드) 발행용 이미지 호스팅 저장소입니다.

## 왜 공개 저장소인가

Instagram Graph API와 Threads API는 이미지를 업로드받지 않고 **공개적으로 접근
가능한 이미지 URL**을 요구합니다. 원고 저장소(blog)는 private이라 raw URL이
열리지 않아, 카드 이미지만 따로 공개해 두는 곳입니다.

**여기에는 카드뉴스 이미지와 쓰레드 상징 이미지만 올립니다.** 원고, 쿠키,
토큰, 계정 정보는 올리지 않습니다. 올라갈 파일 목록은 blog 저장소의
`scripts/publish_sns_images.py`의 `collect_images()` 한 곳에서만 정해지고,
그 규칙은 `scripts/test_publish_sns_images.py`가 지킵니다.

## 경로 규칙

```
posts/<슬러그>/cards/1.png ... 7.png   인스타 카드뉴스
posts/<슬러그>/threads-image.png       쓰레드 상징 이미지
```

raw URL 형식:

```
https://raw.githubusercontent.com/jeusnight-del/blog-sns-images/main/posts/<슬러그>/cards/1.png
```

## 올리는 방법

blog 저장소에서:

```bash
python3 scripts/publish_sns_images.py <슬러그>            # 업로드
python3 scripts/publish_sns_images.py <슬러그> --dry-run  # 목록·URL만 확인
```

## 지우기

발행이 끝난 이미지는 지워도 됩니다. 단 **발행이 완료될 때까지는 접근 가능해야**
합니다 — Meta 쪽이 컨테이너를 처리하는 동안 URL을 다시 읽습니다.
