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
# <a name="input-past-end-of-file"></a><span data-ttu-id="4a5bb-102">輸入超過檔案結尾</span><span class="sxs-lookup"><span data-stu-id="4a5bb-102">Input past end of file</span></span>

<span data-ttu-id="4a5bb-103">`Input`語句正在讀取的檔案是空的，或是使用了所有資料的檔案，或者您使用函式搭配 `EOF` 開啟以進行二進位存取的檔案。</span><span class="sxs-lookup"><span data-stu-id="4a5bb-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4a5bb-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4a5bb-104">To correct this error</span></span>  
  
1. <span data-ttu-id="4a5bb-105">請在 `EOF` 語句之前立即使用函式 `Input` 來偵測檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="4a5bb-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="4a5bb-106">如果開啟檔案進行二進位檔存取，請使用 `Seek` 和 `Loc` 。</span><span class="sxs-lookup"><span data-stu-id="4a5bb-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5bb-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a5bb-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
