---
title: -main (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 2f3c9daf98bfe77ea9462c8126f7a8368016875c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468861"
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
 如果編譯的 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法中包含一個以上的型別，您可以指定哪個型別含有要作為程式進入點的 **Main** 方法。  
  
 在編譯 .exe 檔案時，即可使用此選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [應用程式] 屬性頁。  
  
3.  修改 [啟始物件] 屬性。  
  
     若要以程式設計方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>。  
  
## <a name="example"></a>範例  
 編譯 `t2.cs` 和 `t3.cs`，將 **Main** 方法的位置指定在 `Test2` 中：  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>請參閱

- [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
