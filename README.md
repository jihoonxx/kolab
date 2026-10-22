# KOLAB 홈페이지 (GitHub Pages)

## 1. 처음 올리기 (한 번만)

1. https://github.com 에 가입하거나 로그인합니다.
2. 오른쪽 위 **+ → New repository**를 누릅니다.
   - Repository name: `kolab` (원하는 이름으로 해도 됩니다)
   - **Public**을 선택하고 **Create repository**를 누릅니다.
3. 새 저장소 화면에서 **uploading an existing file** 링크를 누릅니다.
4. 압축을 푼 폴더 **안의 내용 전체**(`index.html`, `gallery.json`, `atlas.json`, `images` 폴더, `.nojekyll`, `README.md`)를 끌어다 놓고 **Commit changes**를 누릅니다.
   - `.nojekyll`이 숨김 파일이라 안 보이면 없어도 사이트는 동작합니다.
5. 저장소의 **Settings → Pages**로 갑니다.
   - Source: **Deploy from a branch**
   - Branch: **main**, 폴더 **/ (root)** → **Save**
6. 1~2분 뒤 같은 화면 위쪽에 주소가 나타납니다.
   예: `https://아이디.github.io/kolab/`

> 저장소 이름을 `아이디.github.io`로 만들면 주소가 `https://아이디.github.io/`가 됩니다.

## 2. 갤러리(moments)에 새 글 올리기

1. 사진을 준비합니다. 파일 이름은 **영문/숫자/하이픈**만 쓰세요.
   예: `2026-10-biochip-1.jpg` (가로 1600~2000px 정도면 충분합니다)
2. 저장소에서 `images/gallery` 폴더로 들어가 **Add file → Upload files**로 사진을 올리고 **Commit changes**를 누릅니다.
3. 저장소 첫 화면에서 `gallery.json`을 열고 연필 아이콘(Edit)을 누릅니다.
4. 맨 위 `[` 바로 아래에 아래 형식으로 한 덩어리를 추가합니다. **끝의 쉼표(,)를 꼭 넣으세요.**

```json
  {
    "date": "2026-10-22",
    "title": "2026 Fall BioChip Conference",
    "caption": "추계 바이오칩학회에서 우주, 수진의 발표.",
    "photos": [
      "images/gallery/2026-10-biochip-1.jpg",
      "images/gallery/2026-10-biochip-2.jpg"
    ]
  },
```

5. **Commit changes**를 누르면 1~2분 뒤 사이트에 반영됩니다. 글은 날짜순으로 자동 정렬됩니다.

**갤러리가 안 보이면**: `gallery.json`의 쉼표나 따옴표가 빠졌을 가능성이 큽니다. https://jsonlint.com 에 내용을 붙여넣어 검사할 수 있습니다.

글을 지우려면 `gallery.json`에서 해당 덩어리(`{ ... },`)를 지우고, 필요하면 사진 파일도 삭제하세요.


## 2-1. 이미지 아틀라스(image atlas)에 연구 이미지 추가하기

1. `images/research` 폴더에 이미지를 올립니다. (예: `liver-chip.jpg`, 가로 1200~2000px 권장)
2. `atlas.json`을 열어 Edit → 원하는 위치에 아래 형식으로 한 덩어리를 추가합니다. **쉼표 주의.**

```json
  {
    "id": "liver-chip",
    "title": "Liver-on-a-chip",
    "type": "fluor",
    "src": "images/research/liver-chip.jpg",
    "note": "Confocal, 20×"
  },
```

- `type`은 다음 중 하나: `fluor`(형광), `r3d`(3D 재구성), `bf`(명시야), `ai`(AI 분석), `dev`(디바이스)
- `note`는 확대 보기에서 제목 옆에 표시됩니다 (비워도 됩니다).
- `atlas.json`의 순서가 화면 순서입니다.
- 첫 화면의 큰 이미지와 연구 분야 이미지는 `images/research/` 안의 같은 이름 파일(예: `tumor-angiogenesis.jpg`)을 **같은 이름의 고해상도 원본으로 덮어쓰면** 바로 바뀝니다.

## 3. 다른 내용 수정하기

구성원, 논문, 뉴스, 연구 내용은 모두 `index.html` 안에 있습니다. GitHub에서 `index.html`을 열고 Edit로 수정할 수 있습니다.

- 뉴스: `const NEWS = [` 부분에 `['2026.10.22','내용'],` 한 줄을 맨 위에 추가
- 논문: `const ALL = [` 부분 (형식: `['저자','제목','저널, 권(호), 쪽',연도]`)
- 대학원생: `const grads = [`, 학부연구생: `const ugs = [`, 졸업생: `const alumni = [`
- 구성원 사진: `images/people/` 폴더에 넣고, `const IMG = {` 목록에 `"이름키": "images/people/파일.jpg"` 추가

## 4. 자체 도메인 연결 (선택)

`kolab.hanyang.ac.kr` 같은 주소를 쓰려면 학교 정보통신처에 DNS(CNAME) 설정을 요청한 뒤,
**Settings → Pages → Custom domain**에 그 주소를 입력하면 됩니다.
