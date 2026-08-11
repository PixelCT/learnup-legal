# 법적 고지 호스팅

앱들의 개인정보처리방침과 이용약관을 GitHub Pages로 게시한다.

**공개 주소**: https://pixelct.github.io/learnup-legal/

각 앱의 메인 저장소는 private이라 Pages를 못 켠다. 그래서 이 public 저장소에
**사본을 두고** 게시한다. 원본은 각 앱 저장소에 있고, 여기 있는 건 생성물이다.

---

## ⚠️ 파일 이름을 바꾸지 말 것

각 파일 주소가 **Play Console의 개인정보처리방침 URL로 등록돼 있다.**
이름을 바꾸거나 옮기면 그 URL이 죽고, 스토어에서 정책 위반으로 잡힌다.
바꿔야 한다면 Play Console의 URL을 먼저 갱신하고 나서 옮긴다.

## 현재 파일

| 파일 | 앱 | 비고 |
|---|---|---|
| `index.html` | — | 앱 목록 허브 |
| `privacy.ko.html` / `privacy.en.html` | 런업 (Learnup) | 앱 접두어가 없다. 이 저장소가 런업 전용이던 시절의 이름이라 그대로 둔다 |
| `terms.ko.html` / `terms.en.html` | 런업 (Learnup) | 〃 |
| `dutchpay-privacy.ko.html` | 더치페이 계산기 | 새 규칙 적용 |

## 새 앱을 추가할 때

**파일명 규칙**: `<앱약칭>-<문서>.<언어>.html`

```
dutchpay-privacy.ko.html
dutchpay-terms.ko.html
myapp-privacy.en.html
```

런업 파일들만 예외다(위 표 참고). 새로 만드는 건 전부 이 규칙을 따른다.

**절차**

1. 앱 저장소에서 문서를 생성한다
   (더치페이의 경우 `dart run tool/gen_privacy_html.dart`)
2. 생성물을 이 저장소에 위 이름으로 복사하고 push
3. `index.html`에 `<section>`을 하나 추가한다 — 앱 이름, 한 줄 설명,
   제공자, 문서 링크
4. 1~2분 뒤 URL이 살아나는지 확인:
   `curl -s -o /dev/null -w "%{http_code}" https://pixelct.github.io/learnup-legal/<파일>`
5. Play Console → 앱 콘텐츠 → 개인정보처리방침에 그 URL 입력

## 내용을 고칠 때

**여기서 직접 고치지 말 것.** 이 파일들은 생성물이라 앱 저장소의 원본과
어긋나면 앱 안에 표시되는 내용과 웹 페이지가 달라진다.

더치페이 계산기의 원본은
`dutch-pay-calculator` 저장소의 `apps/app/lib/core/legal/privacy_policy.dart`이고,
같은 데이터에서 앱 화면과 이 HTML이 함께 생성된다. 거기를 고치고 다시 생성해서
여기에 복사한다.

## 제공자가 앱마다 다를 수 있다

런업은 `PixelCT`, 더치페이 계산기는 `gongjaksoft`처럼 개발자 계정이 다르면
표기명도 다르다. `index.html`에서 앱별로 따로 적는 이유다.
문서 본문의 제공자명은 **Play Console의 개발자 표기명과 일치**해야 한다.
