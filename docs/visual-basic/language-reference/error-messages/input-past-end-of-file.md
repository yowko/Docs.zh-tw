---
title: 輸入超過檔案結尾
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27de462d5d28ee09107d75afe8269e7401c4dc39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
