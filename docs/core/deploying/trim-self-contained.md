---
title: 修剪自包含應用程式
description: 瞭解如何修剪自包含應用以減小其大小。 .NET Core 將運行時與自包含發佈的應用捆綁在一起,並且通常包含更多運行時,因此有必要這樣做。
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665632"
---
# <a name="trim-self-contained-deployments-and-executables"></a>修剪自包含部署及可執行檔

發佈應用程式自包含時,.NET Core 運行時與應用程式捆綁在一起。 這種捆綁為打包的應用程式增加了大量內容。

在部署應用程式時,大小通常是一個重要因素。 保持包應用程式的大小盡可能小通常是應用程式開發人員的目標。

根據應用程式的複雜性,運行應用程式只需要運行時的子集。 這些未使用的運行時部分是不必要的,可以從打包的應用程式修剪。

> [!NOTE]
> 修剪是 .NET Core 3.1 中的實驗功能,_僅適用於_自包含發布的應用程式。

## <a name="trim-your-application"></a>修剪應用程式

下面的範例簡用如何使用[dotnet 發布](../tools/dotnet-publish.md)指令修剪應用程式:

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

修剪功能的工作原理是檢查應用程式二進位檔,以發現和生成所需運行時程式集的圖形。 將修剪未引用的剩餘運行時程式集。

## <a name="trimming-issues-when-using-reflection"></a>使用反射時的修剪問題

在某些情況下,修剪功能將無法檢測引用。 例如,使用反射的應用程式可能會遇到此問題,因為對程式集的依賴項僅在運行時已知。

僅當反射用法依賴於未直接引用的運行時程式集時,修剪才成問題。 請記住,應用程式代碼可能不會直接使用反射,但您引用的第三方程式集可能正在使用它。

當代碼通過反射引用 API 並且不希望連結器修剪包含該 API 的程式集時,可以修改專案檔以從修剪過程中排除程式集。 下面的範例簡報如何防止修剪呼`System.Security`叫的程式集:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a>另請參閱

- [.NET 核心應用程式部署](index.md)
