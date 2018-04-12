---
title: 檔案已經開啟
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a><span data-ttu-id="ad7e5-102">檔案已經開啟</span><span class="sxs-lookup"><span data-stu-id="ad7e5-102">File already open</span></span>
<span data-ttu-id="ad7e5-103">有時檔案必須先關閉另一個之前`FileOpen`或進行其他作業。</span><span class="sxs-lookup"><span data-stu-id="ad7e5-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="ad7e5-104">可能導致本錯誤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="ad7e5-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="ad7e5-105">循序輸出模式`FileOpen`已經開啟的檔案執行作業</span><span class="sxs-lookup"><span data-stu-id="ad7e5-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="ad7e5-106">陳述式參考到開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="ad7e5-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ad7e5-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ad7e5-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="ad7e5-108">關閉檔案再執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="ad7e5-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7e5-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad7e5-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
