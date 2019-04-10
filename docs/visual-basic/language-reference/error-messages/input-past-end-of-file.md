---
title: 輸入超過檔案結尾
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 5da14c7a28ecdcd023fc6439cb6ed64444c1183b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342774"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="2ef1a-102">輸入超過檔案結尾</span><span class="sxs-lookup"><span data-stu-id="2ef1a-102">Input past end of file</span></span>
<span data-ttu-id="2ef1a-103">任一`Input`陳述式會讀取檔案是空的還是會使用所有的資料，或您使用`EOF`進行二進位存取中開啟檔案的函式。</span><span class="sxs-lookup"><span data-stu-id="2ef1a-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ef1a-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2ef1a-104">To correct this error</span></span>  
  
1. <span data-ttu-id="2ef1a-105">使用`EOF`函式之前立即`Input`陳述式來偵測檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="2ef1a-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="2ef1a-106">如果開啟檔案以進行二進位存取，使用`Seek`和`Loc`。</span><span class="sxs-lookup"><span data-stu-id="2ef1a-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ef1a-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ef1a-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
