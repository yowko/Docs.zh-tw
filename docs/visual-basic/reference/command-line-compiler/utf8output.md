---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 0a16cdc535de5ed0619bf080bb4637449b11cfef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403053"
---
# <a name="-utf8output-visual-basic"></a>-utf8output （Visual Basic）
使用 UTF-8 編碼顯示編譯器輸出。  
  
## <a name="syntax"></a>語法  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 這個選項的預設值是 `-utf8output-` ，這表示編譯器輸出不會使用 utf-8 編碼。 指定 `-utf8output` 等同於指定 `-utf8output+`。  
  
## <a name="remarks"></a>備註  
 在某些國際設定中，編譯器輸出無法正確地顯示在主控台中。 在這種情況下，請使用， `-utf8output` 並將編譯器輸出重新導向至檔案。  
  
> [!NOTE]
> 此 `-utf8output` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `In.vb` 並指示編譯器使用 utf-8 編碼來顯示輸出。  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
