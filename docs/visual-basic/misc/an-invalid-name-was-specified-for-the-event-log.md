---
title: 指定給事件記錄檔的名稱無效
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 2b9c934272d0f3392c845dcd2f0062a98dc50c7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940669"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="203f8-102">指定給事件記錄檔的名稱無效</span><span class="sxs-lookup"><span data-stu-id="203f8-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="203f8-103">指定給事件記錄檔的名稱無效。</span><span class="sxs-lookup"><span data-stu-id="203f8-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="203f8-104">這通常是名稱中有無效的字元、檔案名稱空白或檔案名稱太長的結果。</span><span class="sxs-lookup"><span data-stu-id="203f8-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="203f8-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="203f8-105">To correct this error</span></span>  
  
- <span data-ttu-id="203f8-106">如果指定的名稱超過八個字元，請確定該名稱未與其他事件記錄檔的名稱相衝突。</span><span class="sxs-lookup"><span data-stu-id="203f8-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="203f8-107">判斷此名稱是否唯一時，只會評估前八個字元。</span><span class="sxs-lookup"><span data-stu-id="203f8-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="203f8-108">如果提供路徑，請確定已正確地剖析該路徑。</span><span class="sxs-lookup"><span data-stu-id="203f8-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="203f8-109">檢查名稱中沒有無效的字元。</span><span class="sxs-lookup"><span data-stu-id="203f8-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="203f8-110">不能在檔案名稱中使用的字元包括 `<`、 `>`、 `:`、 `"`、 `/`、 `\`和 `|`。</span><span class="sxs-lookup"><span data-stu-id="203f8-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="203f8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="203f8-111">See also</span></span>

- [<span data-ttu-id="203f8-112">如何：剖析檔案路徑</span><span class="sxs-lookup"><span data-stu-id="203f8-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="203f8-113">如何：重新命名檔案</span><span class="sxs-lookup"><span data-stu-id="203f8-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
