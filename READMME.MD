# sass(scss)

## 설치법

1. node 를 설치
2. 터미널에서 npm install -g sass (-g 는 전역 설치 어디서든 sass를 쓸 수 있습니다)
3. sass 바꿀파일이있는폴더/바꿀파일이름.scss:변경파일이있을폴더/변경된파일.css
4. sass --watch 바꿀파일이있는폴더/바꿀파일이름.scss:변경파일이있을폴더/변경된파일.css
   4.1 --watch를 붙이면 파일이 변경될때마다 자동으로 css도 변경해줍니다.
5. sass --style compressed style/main.scss:style/main.css
   5.1 --style compressed (압축의 의미) => 빌드압축하면 공백이런걸 다 지워줘서 용량적으로 효율이좋습니다.
