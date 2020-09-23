---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 2c243b05b7e819691165ef20996691c0bd38ae4a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098861"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror (Visual Basic) 

導致編譯器將第一次出現的警告視為錯誤。  
  
## <a name="syntax"></a>語法  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|+ &#124;-|選擇性。 依預設， `-warnaserror-` 會生效; 警告不會防止編譯器產生輸出檔。 `-warnaserror`選項（與相同 `-warnaserror+` ）會導致將警告視為錯誤。|  
|`numberList`|選擇性。 選項套用之警告識別碼編號的逗號分隔清單 `-warnaserror` 。 如果未指定警告識別碼，選項會 `-warnaserror` 套用至所有警告。|  
  
## <a name="remarks"></a>備註  

 選項會將 `-warnaserror` 所有警告視為錯誤。 通常會回報為警告的任何訊息都會回報為錯誤。 編譯器會將後續出現的警告報告為警告。  
  
 依預設， `-warnaserror-` 會生效，而導致警告僅供參考。 `-warnaserror`選項（與相同 `-warnaserror+` ）會導致將警告視為錯誤。  
  
 如果您只想要將一些特定警告視為錯誤，您可以指定以逗號分隔的警告編號清單來視為錯誤。  
  
> [!NOTE]
> `-warnaserror`選項不會控制警告的顯示方式。 使用 [-nowarn](nowarn.md) 選項來停用警告。  
  
|設定-warnaserror 會將所有警告視為 Visual Studio IDE 中的錯誤|  
|---|  
|1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。 <br />2. 按一下 [ **編譯** ] 索引標籤。<br />3. 請確定未核取 [ **停用所有警告** ] 核取方塊。<br />4. 勾選 [將 **所有警告視為錯誤** ] 核取方塊。|  
  
|Warnaserror 可將特定警告視為 Visual Studio IDE 中的錯誤|  
|---|  
|1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。<br />2. 按一下 [ **編譯** ] 索引標籤。<br />3. 請確定未核取 [ **停用所有警告** ] 核取方塊。<br />4. 請確定未核取 [將 **所有警告視為錯誤** ] 核取方塊。<br />5. 從應視為錯誤的警告旁的**通知**資料行中選取 [**錯誤**]。|  
  
## <a name="example"></a>範例  

 下列程式碼 `In.vb` 會編譯並指示編譯器在第一次出現所找到的每個警告時顯示錯誤。  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>範例  

 下列 `T2.vb` 程式碼只會針對未使用的區域變數（ (42024) 視為錯誤）編譯和處理警告。  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
