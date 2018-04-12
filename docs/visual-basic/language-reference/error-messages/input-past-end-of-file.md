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
# <a name="input-past-end-of-file"></a><span data-ttu-id="4a3f4-102">輸入超過檔案結尾</span><span class="sxs-lookup"><span data-stu-id="4a3f4-102">Input past end of file</span></span>
<span data-ttu-id="4a3f4-103">任一`Input`讀取陳述式是空的檔案，或其中一個會使用所有的資料，或您使用`EOF`針對二進位存取所開啟的檔案具有函式。</span><span class="sxs-lookup"><span data-stu-id="4a3f4-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4a3f4-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4a3f4-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="4a3f4-105">使用`EOF`函式之前，立即`Input`陳述式來偵測檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="4a3f4-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2.  <span data-ttu-id="4a3f4-106">二進位存取開啟檔案時，如果使用`Seek`和`Loc`。</span><span class="sxs-lookup"><span data-stu-id="4a3f4-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3f4-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a3f4-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
