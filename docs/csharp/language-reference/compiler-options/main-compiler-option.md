---
description: -main (C# 編譯器選項)
title: -main (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: c27898de2a7cc2f3c01c51f8de1122e81b2233b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194111"
---
# <a name="-main-c-compiler-options"></a>-main (C# 編譯器選項)

如果有多個類別包含 **Main** 方法，這個選項會指定含有程式進入點的類別。

## <a name="syntax"></a>語法

```console
-main:class
```

## <a name="arguments"></a>引數

 `class`  
 含有 **Main** 方法的類型。  
 提供的類別名稱必須完整。名稱必須包括內含類別的完整命名空間，後面接著類別名稱。 例如，當 `Main` 方法位於 `MyApplication.Core` 命名空間中的 `Program` 類別時，編譯器選項必須是 `-main:MyApplication.Core.Program`。

## <a name="remarks"></a>備註

如果編譯的 [Main](../../programming-guide/main-and-command-args/index.md) 方法中包含一個以上的型別，您可以指定哪個型別含有要作為程式進入點的 **Main** 方法。

此選項適用于編譯 *.exe* 檔時。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性]**** 頁面。

2. 按一下 [應用程式]**** 屬性頁。

3. 修改 [啟始物件]**** 屬性。

    若要以程式設計方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>。

### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a>手動編輯 *.csproj* 檔案以設定這個編譯器選項

您可以藉由編輯 .csproj 檔案並在區段內加入專案來設定此選項 `StartupObject` `PropertyGroup` 。 例如：

```xml
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a>範例

編譯 `t2.cs` 和 `t3.cs`，將 **Main** 方法的位置指定在 `Test2` 中：

```console
csc t2.cs t3.cs -main:Test2
```

## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
