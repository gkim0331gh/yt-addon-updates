# yt-addon-updates

[YT Downloader](https://addons.mozilla.org/) 파이어폭스 확장의 **자동 업데이트 안내 파일**만 담은 저장소.

소스 코드는 여기 없다. 이 저장소가 따로 있는 이유는 하나다 — 파이어폭스가 새 판을 찾아보려면
`updates.json` 과 서명된 `.xpi` 를 **로그인 없이 받을 수 있어야** 하므로 공개되어야 하는데,
그렇다고 소스까지 공개할 이유는 없기 때문이다.

## 담는 것

| 파일 | 무엇 |
|---|---|
| `updates.json` | 어느 판이 최신이고 어디서 받는지 |
| `yt-downloader-<판>.xpi` | Mozilla 서명을 받은 확장 본체 |

## 판을 올릴 때

1. 소스 저장소에서 `build.ps1` 을 돌려 `dist\yt-downloader-firefox-<판>.zip` 을 만든다
2. AMO 에 **자체 배포(On your own)** 로 올려 서명받는다
3. 내려받은 서명본을 `yt-downloader-<판>.xpi` 로 이름을 바꿔 여기에 넣는다
4. 소스 저장소의 `dist\updates.json` 을 여기로 복사한다
5. 커밋하고 올린다

`updates.json` 의 `update_link` 와 `.xpi` 파일 이름이 **글자 하나까지 같아야 한다.**
다르면 파이어폭스는 새 판이 있다는 것만 알고 받지는 못한다.

## 주소

GitHub Pages 를 켜 두었으므로 다음 주소로 열린다.

```
https://gkim0331gh.github.io/yt-addon-updates/updates.json
```

이 주소는 확장의 서명된 파일 안에 박혀 있어 **바꿀 수 없다.** 저장소 이름을 바꾸거나
Pages 를 끄면 이미 배포된 확장들이 조용히 갱신을 멈춘다.
