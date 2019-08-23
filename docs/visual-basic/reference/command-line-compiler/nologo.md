---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 07e1718554b158635b9d8b04958834e804e1fe9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964382"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
在編譯期間隱藏著作權橫幅和參考用訊息。  
  
## <a name="syntax"></a>語法  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>備註  
 如果您指定`-nologo`, 編譯器不會顯示著作權橫幅。 `-nologo` 預設為非作用中。  
  
> [!NOTE]
> 此`-nologo`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。  
  
## <a name="example"></a>範例  
 下列程式碼會`T2.vb`編譯並不顯示著作權橫幅。  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
