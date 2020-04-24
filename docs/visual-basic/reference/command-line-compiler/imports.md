---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 2a1dd19189ff65413255b9bc137e1a7f0227bbe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716654"
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
|`namespaceList`|必要。 要匯入的命名空間清單（以逗號分隔）。|  
  
## <a name="remarks"></a>備註  
 `-imports`選項會匯入目前來源檔案集或任何參考元件中定義的任何命名空間。  
  
 使用`-imports`指定之命名空間中的成員，可供編譯中的所有原始程式碼檔案使用。 使用[Imports 語句（.Net 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ，在單一原始程式碼檔案中使用命名空間。  
  
|若要在 Visual Studio 的整合式開發環境中設定匯入|  
|---|  
|1. 在**方案總管**中選取專案。 按一下 [專案]**** 功能表上的 [屬性]****。 <br />2. 按一下 [**參考**] 索引標籤。<br />3. 在 [**新增使用者匯入**] 按鈕旁邊的方塊中輸入命名空間名稱。<br />4. 按一下 [**新增使用者匯入**] 按鈕。|  
  
## <a name="example"></a>範例  
 當指定時`-imports:system.globalization` ，下列程式碼會進行編譯。 如果沒有它，成功的編譯就必須`Imports System.Globalization`在原始程式碼檔的開頭包含語句，或是屬性必須完整限定為`System.Globalization.CultureInfo.CurrentCulture.Name`。

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
