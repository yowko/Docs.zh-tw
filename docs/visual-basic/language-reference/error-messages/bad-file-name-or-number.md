---
title: "不正確的檔名或數目"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a>不正確的檔名或數目
嘗試存取指定的檔案時發生錯誤。 此錯誤的可能原因包括：  
  
-   陳述式中未指定檔名或數目與檔案參考`FileOpen`或陳述式中指定`FileOpen`陳述式，但卻是之後關閉。  
  
-   陳述式所參考的檔案與超出範圍的檔案數字的數字。  
  
-   陳述式參考的檔案名稱或不是有效的數字。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確認檔案名稱指定在`FileOpen`陳述式。 請注意，如果您叫用`FileClose`陳述式沒有引數，您可能會不小心關閉所有開啟的檔案。  
  
2.  如果您的程式碼會利用演算法產生檔案數目，請確定使用數字。  
  
3.  請檢查檔案名稱，以確保它們符合作業系統慣例。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
