# [CMD] 더미파일 만들기

레빗엠큐 테스트를 위한 더미파일을 만들어 보았다. 방법은 아래와 같다.

1. cmd창을 연다.
2. 파일을 만들고 싶은 폴더로 이동한다 cd명령어 사용
3. 해당 명령어를 작성한다.

```
// 200MB 더미파일 생성
fsutil file createnew 200MB_dummy_file.bin 209715200

// 500MB 더미파일 생성
fsutil file createnew 500MB_dummy_file.bin 524288000

// 1GB 더미파일 생성
fsutil file createnew 1GB_dummy_file.bin 1048576000
```

#### fsutil 명령어를 사용해서 쉽게 더미파일을 만들고 테스트가 가능하다!! 👍👍👍
