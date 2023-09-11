# SimpleRename
能够批量以序列方式重命名文件夹下所有的图片命名。
@echo off
setlocal enabledelayedexpansion

rem 设置计数器初始值
set count=1

rem 获取脚本文件名（包括扩展名）
set scriptName=%~nx0

rem 遍历当前文件夹下的所有文件
for %%f in (*) do (
    rem 检查文件名是否与脚本文件名相同
    if "%%f" neq "!scriptName!" (
        rem 构建新的文件名（数字格式）
        set "newName=!count!"
        
        rem 重命名文件
        ren "%%f" "!newName!%%~xf"
        
        rem 增加计数器
        set /a "count+=1"
    )
)

endlocal
