---
title: 檔案已經開啟
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 401801c7c9072ce11f9eafdb84f2b377669ae545
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301317"
---
# <a name="file-already-open"></a><span data-ttu-id="4376d-102">檔案已經開啟</span><span class="sxs-lookup"><span data-stu-id="4376d-102">File already open</span></span>
<span data-ttu-id="4376d-103">有時候必須先關閉檔案之前另一個`FileOpen`或進行其他作業。</span><span class="sxs-lookup"><span data-stu-id="4376d-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="4376d-104">可能導致本錯誤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="4376d-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="4376d-105">循序輸出模式`FileOpen`已經開啟的檔案執行作業</span><span class="sxs-lookup"><span data-stu-id="4376d-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="4376d-106">陳述式參考開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="4376d-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4376d-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4376d-107">To correct this error</span></span>  
  
1. <span data-ttu-id="4376d-108">關閉檔案再執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="4376d-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4376d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4376d-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
