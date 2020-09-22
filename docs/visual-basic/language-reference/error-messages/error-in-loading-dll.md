---
title: 載入 DLL 時發生錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 35733fe2e20d46207f6cfdaee32f6559fceed6eb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874386"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="7f866-102">載入 DLL 時發生錯誤 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f866-102">Error in loading DLL (Visual Basic)</span></span>

<span data-ttu-id="7f866-103">動態連結程式庫 (DLL) 是在語句的子句中指定的程式庫 `Lib` `Declare` 。</span><span class="sxs-lookup"><span data-stu-id="7f866-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="7f866-104">此錯誤的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="7f866-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="7f866-105">檔案不是 DLL 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7f866-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="7f866-106">檔案不是 Microsoft Windows DLL。</span><span class="sxs-lookup"><span data-stu-id="7f866-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="7f866-107">DLL 參考不存在的另一個 DLL。</span><span class="sxs-lookup"><span data-stu-id="7f866-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="7f866-108">DLL 或參考的 DLL 不在路徑中指定的目錄中。</span><span class="sxs-lookup"><span data-stu-id="7f866-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7f866-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7f866-109">To correct this error</span></span>  
  
- <span data-ttu-id="7f866-110">如果檔案是來源文字檔，而不是 DLL 可執行檔，則必須將它編譯並連結至 DLL 可執行檔表單。</span><span class="sxs-lookup"><span data-stu-id="7f866-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="7f866-111">如果檔案不是 Microsoft Windows DLL，請取得 Microsoft Windows 對等專案。</span><span class="sxs-lookup"><span data-stu-id="7f866-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="7f866-112">如果 DLL 參考不存在的另一個 DLL，請取得參考的 DLL，並使其可供使用。</span><span class="sxs-lookup"><span data-stu-id="7f866-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="7f866-113">如果 DLL 或參考的 DLL 不在路徑所指定的目錄中，請將 DLL 移至參考的目錄。</span><span class="sxs-lookup"><span data-stu-id="7f866-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f866-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f866-114">See also</span></span>

- [<span data-ttu-id="7f866-115">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="7f866-115">Declare Statement</span></span>](../statements/declare-statement.md)
