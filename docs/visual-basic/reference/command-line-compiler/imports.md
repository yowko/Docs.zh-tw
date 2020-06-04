---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: cc9fc222843bdfe8e49d2d291dc36ff3e0c63fc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408591"
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
 選項會匯 `-imports` 入目前來源檔案集或任何參考元件中定義的任何命名空間。  
  
 使用指定之命名空間中的成員， `-imports` 可供編譯中的所有原始程式碼檔案使用。 使用[Imports 語句（.Net 命名空間和類型）](../../language-reference/statements/imports-statement-net-namespace-and-type.md) ，在單一原始程式碼檔案中使用命名空間。  
  
|若要在 Visual Studio 的整合式開發環境中設定匯入|  
|---|  
|1. 在**方案總管**中選取專案。 按一下 [專案]**** 功能表上的 [屬性]****。 <br />2. 按一下 [**參考**] 索引標籤。<br />3. 在 [**新增使用者匯入**] 按鈕旁邊的方塊中輸入命名空間名稱。<br />4. 按一下 [**新增使用者匯入**] 按鈕。|  
  
## <a name="example"></a>範例  
 當指定時，下列 `-imports:system.globalization` 程式碼會進行編譯。 如果沒有它，成功的編譯就必須在 `Imports System.Globalization` 原始程式碼檔的開頭包含語句，或是屬性必須完整限定為 `System.Globalization.CultureInfo.CurrentCulture.Name` 。

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [References 與 Imports 陳述式](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
