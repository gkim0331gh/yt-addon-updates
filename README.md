# yt-addon-updates

MADE WITH AI ASSISTANCE · FOR PERSONAL USE ONLY · NOT RESPONSIBLE FOR ANY LEGAL OR MORAL DISADVANTAGES BY USING THIS REPOSITORY

[YT Downloader](https://addons.mozilla.org/) 파이어폭스 확장의 **자동 업데이트 안내 파일**만 담은 저장소.

소스 코드는 여기 없다. 이 저장소가 따로 있는 이유는 하나다 — 파이어폭스가 새 판을 찾아보려면
`updates.json` 과 서명된 `.xpi` 를 **로그인 없이 받을 수 있어야** 하므로 공개되어야 하는데,
그렇다고 소스까지 공개할 이유는 없기 때문이다.

## 받으려면 — 두 개가 필요하다

확장만 깔면 "로컬 프로그램과의 연결이 끊어졌다"가 뜬다.
확장은 화면일 뿐이고, 실제로 받는 일은 `ytdl-host.exe` 가 한다.
확장은 그 프로그램을 스스로 깔 수 없다 — 브라우저가 막아 둔 선이다.

1. **[Releases](../../releases)** 에서 `ytdl-host.exe` 를 받아 **두 번 누른다**
   스스로 자리를 잡고, 브라우저에 등록하고, yt-dlp 와 ffmpeg 를 받아온다 (약 300MB)
2. 브라우저에 확장을 설치한다
   - **Firefox** — [`yt-downloader-2.6.0.xpi`](https://gkim0331gh.github.io/yt-addon-updates/yt-downloader-2.6.0.xpi) 를 열면 설치된다. 이후 자동 갱신된다
   - **Chrome / Edge** — Releases 의 `yt-downloader-chrome-<판>.zip` 을 풀고,
     `chrome://extensions` → 개발자 모드 → [압축해제된 확장 프로그램을 로드]

윈도우가 "PC 를 보호했습니다"를 띄우면 코드 서명 인증서가 없어서다.
`추가 정보` → `실행` 을 누르면 된다.

지울 때는 윈도우 **설정 → 앱** 에서 `YT Downloader (로컬 프로그램)` 를 제거하면 된다.
확장은 브라우저에서 따로 지운다.

> 크롬은 자동 갱신이 없다. 웹 스토어 정책이 영상 내려받기 확장을 금지해 올릴 수 없기
> 때문이다. 새 판이 나오면 zip 을 다시 받아야 한다.

## 담는 것

| 파일 | 무엇 |
|---|---|
| `updates.json` | 어느 판이 최신이고 어디서 받는지 |
| `yt-downloader-<판>.xpi` | Mozilla 서명을 받은 확장 본체 |
| Releases | `ytdl-host.exe` 와 크롬용 zip. 실행 파일은 판마다 쌓이므로 git 기록에 넣지 않는다 |

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
