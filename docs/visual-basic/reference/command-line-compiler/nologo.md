---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 5557d681c5e6901592936efd35b3c552d43e39b0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097666"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic) 

在編譯期間隱藏著作權橫幅和參考用訊息的顯示。  
  
## <a name="syntax"></a>語法  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>備註  

 如果您指定 `-nologo` ，編譯器就不會顯示著作權橫幅。 `-nologo` 預設為非作用中。  
  
> [!NOTE]
> `-nologo`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  

 下列程式碼 `T2.vb` 會進行編譯，而且不會顯示著作權橫幅。  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
