---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 03dc98c45a894304a67765c3e49cd19bbb089c8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335440"
---
# <a name="-nologo-visual-basic"></a>-nologo （Visual Basic）
在編譯期間隱藏著作權橫幅和參考用訊息。  
  
## <a name="syntax"></a>語法  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>備註  
 如果您指定 `-nologo`，編譯器不會顯示著作權橫幅。 `-nologo` 預設為非作用中。  
  
> [!NOTE]
> Visual Studio 開發環境中無法使用 [`-nologo`] 選項;只有在從命令列編譯時，才可以使用它。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `T2.vb`，且不會顯示著作權橫幅。  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
