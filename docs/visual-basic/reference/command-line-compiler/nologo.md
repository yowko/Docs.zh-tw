---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: d1307603ebc06b4eb4c3786f1cd2fb432c0cf636
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360458"
---
# <a name="-nologo-visual-basic"></a>-nologo （Visual Basic）
在編譯期間隱藏著作權橫幅和參考用訊息。  
  
## <a name="syntax"></a>語法  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>備註  
 如果您指定 `-nologo` ，編譯器不會顯示著作權橫幅。 `-nologo` 預設為非作用中。  
  
> [!NOTE]
> 此 `-nologo` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  
 下列程式碼 `T2.vb` 會編譯並不顯示著作權橫幅。  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
