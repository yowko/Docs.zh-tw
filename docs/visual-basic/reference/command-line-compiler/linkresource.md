---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 8c4f753f94aedaf0a4f997a3f9b99fb3f417abf8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065680"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic) 

建立與 Managed 資源的連結。  
  
## <a name="syntax"></a>語法  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

或  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引數  

 `filename`  
 必要。 要連結至元件的資源檔。 如果檔案名包含空格，請用引號括住名稱 ( "" ) 。  
  
 `identifier`  
 選擇性。 資源的邏輯名稱。 用來載入資源的名稱。 預設值是檔案的名稱。 您可以選擇性地指定檔案是否在組件資訊清單中為公用或私用，例如： `-linkres:filename.res,myname.res,public` 。 依預設，在 `filename` 元件中是公用的。  
  
## <a name="remarks"></a>備註  

 `-linkresource`選項不會將資源檔內嵌在輸出檔中，請使用 `-resource` 選項來執行此動作。  
  
 `-linkresource`選項需要的 `-target` 選項之一除外 `-target:module` 。  
  
 例如，如果 `filename` 是 .NET Framework 資源檔（例如，由 [Resgen.exe (資源檔 ](../../../framework/tools/resgen-exe-resource-file-generator.md) 產生器) 或在開發環境中所建立），則可以使用命名空間中的成員進行存取 <xref:System.Resources> 。  (如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager> 。 ) 若要在執行時間存取所有其他資源，請使用在類別中以開頭的方法 `GetManifestResource` <xref:System.Reflection.Assembly> 。  
  
 檔案名可以是任何檔案格式。 例如，您可能需要產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。  
  
 `-linkresource` 的簡短形式為 `-linkres`。  
  
> [!NOTE]
> `-linkresource`選項無法在 Visual Studio 開發環境中使用; 只有當您從命令列進行編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  

 下列程式碼會編譯 `in.vb` 並連結至資源檔 `rf.resource` 。  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-目標 (Visual Basic) ](target.md)
- [-resource (Visual Basic) ](resource.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
