---
title: 不正確的檔案模式
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: d3d0ebd003f178567ec9e9b19d6baccb8bc15f60
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819979"
---
# <a name="bad-file-mode"></a><span data-ttu-id="c2a58-102">不正確的檔案模式</span><span class="sxs-lookup"><span data-stu-id="c2a58-102">Bad file mode</span></span>
<span data-ttu-id="c2a58-103">用於管理檔案內容的陳述式必須是適用於開啟檔案的模式。</span><span class="sxs-lookup"><span data-stu-id="c2a58-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="c2a58-104">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="c2a58-104">Possible causes include:</span></span>  
  
-   <span data-ttu-id="c2a58-105">A`FilePutObject`或`FileGetObject`陳述式指定循序檔案。</span><span class="sxs-lookup"><span data-stu-id="c2a58-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
-   <span data-ttu-id="c2a58-106">A`Print`陳述式會指定檔案，而不開啟以供存取模式`Output`或`Append`。</span><span class="sxs-lookup"><span data-stu-id="c2a58-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
-   <span data-ttu-id="c2a58-107">`Input`陳述式會指定檔案，而不開啟以供存取模式 `Input`</span><span class="sxs-lookup"><span data-stu-id="c2a58-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
-   <span data-ttu-id="c2a58-108">嘗試寫入唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="c2a58-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c2a58-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c2a58-109">To correct this error</span></span>  
  
-   <span data-ttu-id="c2a58-110">請確定`FilePutObject`並`FileGetObject`只會參考到開啟的檔案`Random`或`Binary`存取。</span><span class="sxs-lookup"><span data-stu-id="c2a58-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
-   <span data-ttu-id="c2a58-111">請確定`Print`指定的其中一個開啟的檔案`Output`或`Append`存取模式。</span><span class="sxs-lookup"><span data-stu-id="c2a58-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="c2a58-112">如果不是，將資料放在檔案中，使用不同的陳述式，或重新開啟適當的模式中的檔案。</span><span class="sxs-lookup"><span data-stu-id="c2a58-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="c2a58-113">請確定`Input`指定檔案，開啟以供`Input`。</span><span class="sxs-lookup"><span data-stu-id="c2a58-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="c2a58-114">否則，請使用不同的陳述式來將資料放在檔案或重新開啟適當的模式中的檔案。</span><span class="sxs-lookup"><span data-stu-id="c2a58-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="c2a58-115">如果您要寫入唯讀檔案，變更檔案的讀取/寫入狀態，或請勿嘗試將寫入其中。</span><span class="sxs-lookup"><span data-stu-id="c2a58-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
-   <span data-ttu-id="c2a58-116">使用 `My.Computer.FileSystem` 物件中可用的功能。</span><span class="sxs-lookup"><span data-stu-id="c2a58-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a58-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2a58-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="c2a58-118">疑難排解：讀取和寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="c2a58-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
