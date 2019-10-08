---
title: -warnaserror （Visual Basic）
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 8af6d3ef4efecd53dcf38c33d0aa2cf182f07d30
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004657"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror （Visual Basic）
使編譯器將第一次出現的警告視為錯誤。  
  
## <a name="syntax"></a>語法  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|+ &#124; -|選擇性。 根據預設，`-warnaserror-` 會生效;警告不會防止編譯器產生輸出檔。 @No__t-0 選項（與 `-warnaserror+` 相同）會導致警告視為錯誤。|  
|`numberList`|選擇性。 以逗號分隔的清單，其中列出 `-warnaserror` 選項所套用的警告識別碼編號。 如果未指定警告識別碼，則 `-warnaserror` 選項會套用至所有警告。|  
  
## <a name="remarks"></a>備註  
 @No__t-0 選項會將所有警告視為錯誤。 通常會回報為警告的任何訊息會改為回報為錯誤。 編譯器會報告與警告相同的後續出現的警告。  
  
 根據預設，`-warnaserror-` 會生效，這會導致警告僅做為參考之用。 @No__t-0 選項（與 `-warnaserror+` 相同）會導致警告視為錯誤。  
  
 如果您只想要將幾個特定警告視為錯誤，您可以指定以逗號分隔的警告編號清單來視為錯誤。  
  
> [!NOTE]
> @No__t-0 選項不會控制警告的顯示方式。 使用[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)選項可停用警告。  
  
|若要設定-warnaserror 以將所有警告視為錯誤在 Visual Studio IDE 中|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.請確定未核取 [**停用所有警告**] 核取方塊。<br />4.勾選 [將**所有警告視為錯誤**] 核取方塊。|  
  
|若要設定-warnaserror 以將特定警告視為 Visual Studio IDE 中的錯誤|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。<br />2.按一下 [編譯] 索引標籤。<br />3.請確定未核取 [**停用所有警告**] 核取方塊。<br />4.請確定未核取 [將**所有警告視為錯誤**] 核取方塊。<br />5.從應視為錯誤的警告旁的**通知**資料行中，選取 [**錯誤**]。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `In.vb`，並指示編譯器在第一次出現的每個警告發現時顯示錯誤。  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `T2.vb`，並只會將未使用的區域變數（42024）的警告視為錯誤。  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
