---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 1b9cedc3e45795a66c203d4c86bb071045a1d3f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550470"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
在編譯期間隱藏著作權橫幅和參考用訊息的顯示。  
  
## <a name="syntax"></a>語法  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>備註  
 如果您指定`-nologo`，編譯器不顯示著作權橫幅。 `-nologo` 預設為非作用中。  
  
> [!NOTE]
>  `-nologo`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`並不顯示著作權橫幅。  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
