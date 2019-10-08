---
title: -imports （Visual Basic）
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 929e24a1ffd02d4e21ab1b925ddd59050b5d3cc4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005570"
---
# <a name="-imports-visual-basic"></a>-imports （Visual Basic）
從指定的元件匯入命名空間。  
  
## <a name="syntax"></a>語法  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`namespaceList`|必要項。 要匯入的命名空間清單（以逗號分隔）。|  
  
## <a name="remarks"></a>備註  
 @No__t-0 選項會匯入目前原始程式檔集或任何參考元件中定義的任何命名空間。  
  
 在指定的命名空間中，具有 `-imports` 的成員可供編譯中的所有原始程式碼檔案使用。 使用[Imports 語句（.Net 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ，在單一原始程式碼檔案中使用命名空間。  
  
|在 Visual Studio 的整合式開發環境中設定/imports|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [參考] 節點。<br />3.在 [**新增使用者匯入**] 按鈕旁邊的方塊中輸入命名空間名稱。<br />4.按一下 [**新增使用者匯入**] 按鈕。|  
  
## <a name="example"></a>範例  
 當指定 `/imports:system.globalization` 時，下列程式碼會進行編譯。 如果沒有它，成功的編譯就必須在原始程式碼檔的開頭包含 @no__t 0 的語句，或是屬性必須完整限定為 `System.Globalization.CultureInfo.CurrentCulture.Name`。

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
