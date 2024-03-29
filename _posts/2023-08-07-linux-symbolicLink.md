---
title: "Linux 서버에서 심볼릭 링크 설정 방법"
date: 2023-08-07
categories: linux
---

### Linux 서버에서 심볼릭 링크 설정 방법

---

Linux 심볼릭 링크는 Windows의 바로가기와 같은 링크를 만드는 기능이다.
이번에는 Linux 서버에서 심볼릭 링크 설정 방법을 알아보도록 하겠다.

```
* 심볼릭 링크 생성
# ln -s [경로] [링크명]
# ln -s /nas/storage/data data

* 심볼릭 링크 삭제
# rm data(심볼릭 링크명)
```

심볼릭 링크가 생성되면 해당 디렉토리에 링크명 -> 경로 형식으로 표시가 된다
ex) data -> /nas/storage/data

만약 특정 디렉토리에 많은 데이터가 쌓이지만 해당 서버 용량이 부족한 경우
위와 같이 NAS나 SAN 등의 스토리지 경로로 심볼릭 링크를 설정하면 관리가 가능하다.
