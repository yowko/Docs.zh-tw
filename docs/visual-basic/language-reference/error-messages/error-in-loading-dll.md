---
title: "載入 DLL 時發生錯誤 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc557dcc6709178b6519adb56f31debcbd1d1c39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="19d3a-102">載入 DLL 時發生錯誤 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19d3a-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="19d3a-103">動態連結程式庫 (DLL) 是程式庫中指定`Lib`子句`Declare`陳述式。</span><span class="sxs-lookup"><span data-stu-id="19d3a-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="19d3a-104">這項錯誤的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="19d3a-104">Possible causes for this error include:</span></span>  
  
-   <span data-ttu-id="19d3a-105">檔案不是可執行檔的 DLL。</span><span class="sxs-lookup"><span data-stu-id="19d3a-105">The file is not DLL executable.</span></span>  
  
-   <span data-ttu-id="19d3a-106">檔案不是 Microsoft Windows DLL。</span><span class="sxs-lookup"><span data-stu-id="19d3a-106">The file is not a Microsoft Windows DLL.</span></span>  
  
-   <span data-ttu-id="19d3a-107">DLL 會參考不存在的另一個 DLL。</span><span class="sxs-lookup"><span data-stu-id="19d3a-107">The DLL references another DLL that is not present.</span></span>  
  
-   <span data-ttu-id="19d3a-108">DLL 或參考的 DLL 不在路徑中指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="19d3a-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="19d3a-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="19d3a-109">To correct this error</span></span>  
  
-   <span data-ttu-id="19d3a-110">如果是檔案的原始程式文字檔案，因此不 DLL 的可執行檔，它必須編譯並連結到 DLL 可執行檔格式。</span><span class="sxs-lookup"><span data-stu-id="19d3a-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
-   <span data-ttu-id="19d3a-111">如果不是 Microsoft Windows DLL 檔案，取得對等的 Microsoft Windows。</span><span class="sxs-lookup"><span data-stu-id="19d3a-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
-   <span data-ttu-id="19d3a-112">如果 DLL 參考不存在的另一個 DLL 時，取得參考的 DLL，並將其提供。</span><span class="sxs-lookup"><span data-stu-id="19d3a-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
-   <span data-ttu-id="19d3a-113">如果 DLL 或參考的 DLL 不指定路徑的目錄中，請將 DLL 移到參考的目錄。</span><span class="sxs-lookup"><span data-stu-id="19d3a-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d3a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19d3a-114">See Also</span></span>  
 [<span data-ttu-id="19d3a-115">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="19d3a-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
