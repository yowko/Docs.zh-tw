---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: c5bf988d819a8df8aed99588abbb30e19d14b1ac
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084979"
---
# <a name="-verbose"></a>-verbose

導致編譯器產生詳細資訊狀態和錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>引數  

 `+` &#124; `-`  
 選擇性。 指定與 `-verbose` 指定相同 `-verbose+` ，這會導致編譯器發出詳細資訊訊息。 此選項的預設值為 `-verbose-` 。  
  
## <a name="remarks"></a>備註  

 `-verbose`選項會顯示編譯器所發出之錯誤總數的相關資訊、報告模組正在載入哪些元件，以及顯示目前正在編譯的檔案。  
  
> [!NOTE]
> `-verbose`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  

 下列程式碼會編譯 `In.vb` 並指示編譯器顯示詳細資訊狀態資訊。  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
