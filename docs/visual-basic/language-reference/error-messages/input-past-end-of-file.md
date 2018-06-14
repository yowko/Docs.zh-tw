---
title: 輸入超過檔案結尾
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: abd5f5c6e5df262d1deadd74f0a146a8d436ceb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586737"
---
# <a name="input-past-end-of-file"></a>輸入超過檔案結尾
任一`Input`讀取陳述式是空的檔案，或其中一個會使用所有的資料，或您使用`EOF`針對二進位存取所開啟的檔案具有函式。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  使用`EOF`函式之前，立即`Input`陳述式來偵測檔案的結尾。  
  
2.  二進位存取開啟檔案時，如果使用`Seek`和`Loc`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
