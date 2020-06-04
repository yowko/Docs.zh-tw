---
title: 載入 DLL 時發生錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: fd2e425f2dd3f4127cd777d4a1f7ab9809de9d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409619"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="9c698-102">載入 DLL 時發生錯誤 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c698-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="9c698-103">動態連結程式庫（DLL）是在語句的子句中指定的程式庫 `Lib` `Declare` 。</span><span class="sxs-lookup"><span data-stu-id="9c698-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="9c698-104">此錯誤的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="9c698-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="9c698-105">檔案不是 DLL 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="9c698-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="9c698-106">檔案不是 Microsoft Windows DLL。</span><span class="sxs-lookup"><span data-stu-id="9c698-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="9c698-107">DLL 參考另一個不存在的 DLL。</span><span class="sxs-lookup"><span data-stu-id="9c698-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="9c698-108">DLL 或參考的 DLL 不在路徑中指定的目錄中。</span><span class="sxs-lookup"><span data-stu-id="9c698-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c698-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9c698-109">To correct this error</span></span>  
  
- <span data-ttu-id="9c698-110">如果檔案是原始程式檔，而不是 DLL 可執行檔，則必須編譯並連結至 DLL 可執行檔表單。</span><span class="sxs-lookup"><span data-stu-id="9c698-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="9c698-111">如果檔案不是 Microsoft Windows DLL，請取得 Microsoft Windows 對等的。</span><span class="sxs-lookup"><span data-stu-id="9c698-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="9c698-112">如果 DLL 參考另一個不存在的 DLL，請取得參考的 DLL 並使其可供使用。</span><span class="sxs-lookup"><span data-stu-id="9c698-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="9c698-113">如果 DLL 或參考的 DLL 不在路徑所指定的目錄中，請將 DLL 移至參考的目錄。</span><span class="sxs-lookup"><span data-stu-id="9c698-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c698-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c698-114">See also</span></span>

- [<span data-ttu-id="9c698-115">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="9c698-115">Declare Statement</span></span>](../statements/declare-statement.md)
