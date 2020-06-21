# transfer.sh

> [transfer 官网](https://transfer.sh/)
windows

```powershell
invoke-webrequest -method put -infile .\test.txt https://transfer.sh/test.txt
```

linux

```bash
curl --upload-file ./hello.txt https://transfer.sh/hello.txt 
curl -H "Max-Downloads: 1" -H "Max-Days: 5" --upload-file ./hello.txt https://transfer.sh/hello.txt 

curl https://transfer.sh/66nb8/hello.txt -o hello.txt
```

## 一级标题1

- [x] 显示
- [ ] 显示2
