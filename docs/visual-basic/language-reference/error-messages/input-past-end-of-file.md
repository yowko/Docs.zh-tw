---
title: 輸入超過檔案結尾
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: c0cb0373fb0652e9600ac8651661708414561aca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873968"
---
# <a name="input-past-end-of-file"></a>輸入超過檔案結尾

`Input`語句正在讀取的檔案是空的，或是使用了所有資料的檔案，或者您使用函式搭配 `EOF` 開啟以進行二進位存取的檔案。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請在 `EOF` 語句之前立即使用函式 `Input` 來偵測檔案結尾。  
  
2. 如果開啟檔案進行二進位檔存取，請使用 `Seek` 和 `Loc` 。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
