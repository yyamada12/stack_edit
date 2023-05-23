# JacksonでOptionalを使うとどうなるか


## json → java class

jsonでundefined の場合
→ null

jsonでnullの場合
→ Optional.empty()

jasonで値が設定されている場合
→ Optionalで値が入っている状態

## java class → json
デフォルトだと、Optionalは
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMDk3MjcxOTVdfQ==
-->