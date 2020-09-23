---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 7ded2b7d102430d8d4e545da5ab6ce8bafe3609e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095417"
---
# <a name="-recurse"></a>-recurse

編譯指定目錄或專案目錄之所有子目錄中的原始程式碼檔。  
  
## <a name="syntax"></a>語法  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引數  

 `dir`  
 選擇性。 您想要開始搜尋的目錄。 如果未指定，則會在專案目錄中開始搜尋。  
  
 `file`  
 必要。 要搜尋的檔案。 允許萬用字元。  
  
## <a name="remarks"></a>備註  

 您可以在檔案名中使用萬用字元，來編譯專案目錄中的所有相符檔案，而不使用 `-recurse` 。 如果未指定輸出檔名稱，編譯器會以第一個處理的輸入檔案為基礎來處理輸出檔名稱。 這通常是在依字母順序查看時，編譯的檔案清單中的第一個檔案。 基於這個理由，最好使用選項來指定輸出檔 `-out` 。  
  
> [!NOTE]
> `-recurse`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  

 下列命令會編譯目前目錄中的所有 Visual Basic 檔案。  
  
```console
vbc *.vb  
```  
  
 下列命令會編譯目錄中的所有 Visual Basic 檔案，以及 `Test\ABC` 其下的任何目錄，然後產生 `Test.ABC.dll` 。  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-out (Visual Basic) ](out.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
