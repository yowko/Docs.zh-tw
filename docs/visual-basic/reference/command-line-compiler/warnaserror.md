---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: c06326a250fba0de2f63e13672b4fffbfa8a07f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835059"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror (Visual Basic)
可讓編譯器在第一個出現的警告視為錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|+ &#124; -|選擇性。 根據預設，`-warnaserror-`是作用中; 警告不會防止編譯器產生的輸出檔。 `-warnaserror`相同的選項為`-warnaserror+`，會導致警告視為錯誤。|  
|`numberList`|選擇性。 以逗號分隔的清單，警告識別碼的數字的`-warnaserror`選項會套用。 如果未不指定任何警告識別碼，則`-warnaserror`選項會套用至所有警告。|  
  
## <a name="remarks"></a>備註  
 `-warnaserror`選項會將所有警告都視為錯誤。 任何會報告為警告而是會回報為錯誤的訊息。 編譯器會報告為警告的相同警告後面出現。  
  
 根據預設，`-warnaserror-`會生效，這會導致只是告知性警告。 `-warnaserror`相同的選項為`-warnaserror+`，會導致警告視為錯誤。  
  
 如果您想只將少數特定警告視為錯誤，您可以指定以逗號分隔的警告編號清單視為錯誤。  
  
> [!NOTE]
>  `-warnaserror`選項不會控制警告的顯示方式。 使用[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)停用警告的選項。  
  
|若要設定將所有警告視為錯誤，Visual Studio IDE 中-warnaserror|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.請確定**停用所有警告**未核取核取方塊。<br />4.請檢查**將所有警告視為錯誤**核取方塊。|  
  
|若要設定將特定警告視為錯誤，Visual Studio IDE 中-warnaserror|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。<br />2.按一下 [編譯] 索引標籤。<br />3.請確定**停用所有警告**未核取核取方塊。<br />4.請確定**將所有警告視為錯誤**未核取核取方塊。<br />5.選取 **錯誤**從**通知**應該視為錯誤的警告相鄰的資料行。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`和指示編譯器將會顯示錯誤，它會尋找每個警告的第一個相符項目。  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`和未使用的本機變數 (42024) 警告視為錯誤。  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
