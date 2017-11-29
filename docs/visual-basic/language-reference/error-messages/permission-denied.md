---
title: "使用權限遭拒 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5d7965ebd42cb3e56d66966d035be9ba3d3957c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="b876f-102">使用權限遭拒 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b876f-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="b876f-103">嘗試寫入防寫保護的磁碟，或存取已鎖定的檔案。</span><span class="sxs-lookup"><span data-stu-id="b876f-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b876f-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b876f-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="b876f-105">若要開啟防寫保護的檔案，請變更檔案的防寫保護屬性。</span><span class="sxs-lookup"><span data-stu-id="b876f-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2.  <span data-ttu-id="b876f-106">請確定其他處理序不會鎖定檔案，並等待直到其他處理序釋放它為止，開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="b876f-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3.  <span data-ttu-id="b876f-107">若要存取登錄，請檢查您的使用者權限包含這種類型的登錄存取權。</span><span class="sxs-lookup"><span data-stu-id="b876f-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b876f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b876f-108">See Also</span></span>  
 [<span data-ttu-id="b876f-109">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="b876f-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
