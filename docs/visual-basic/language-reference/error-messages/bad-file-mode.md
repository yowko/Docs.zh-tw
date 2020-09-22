---
title: 不正確的檔案模式
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 99b84902ddf032f2ecb6e26400e200bea862dfdf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875155"
---
# <a name="bad-file-mode"></a><span data-ttu-id="d11ad-102">不正確的檔案模式</span><span class="sxs-lookup"><span data-stu-id="d11ad-102">Bad file mode</span></span>

<span data-ttu-id="d11ad-103">用於操作檔案內容的語句，必須適合用來開啟檔案的模式。</span><span class="sxs-lookup"><span data-stu-id="d11ad-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="d11ad-104">可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="d11ad-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="d11ad-105">`FilePutObject`或 `FileGetObject` 語句會指定順序檔案。</span><span class="sxs-lookup"><span data-stu-id="d11ad-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="d11ad-106">`Print`語句會指定針對或以外的存取模式開啟的檔案 `Output` `Append` 。</span><span class="sxs-lookup"><span data-stu-id="d11ad-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="d11ad-107">`Input`語句會指定為存取模式開啟的檔案，而非`Input`</span><span class="sxs-lookup"><span data-stu-id="d11ad-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="d11ad-108">嘗試寫入至唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="d11ad-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d11ad-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d11ad-109">To correct this error</span></span>  
  
- <span data-ttu-id="d11ad-110">請確定 `FilePutObject` 並 `FileGetObject` 只參照開啟或存取的檔案 `Random` `Binary` 。</span><span class="sxs-lookup"><span data-stu-id="d11ad-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="d11ad-111">請確定 `Print` 針對 `Output` 或存取模式指定開啟的檔案 `Append` 。</span><span class="sxs-lookup"><span data-stu-id="d11ad-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="d11ad-112">如果沒有，請使用不同的語句將資料放入檔案中，或在適當的模式中重新開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="d11ad-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="d11ad-113">請確定 `Input` 指定開啟的檔案 `Input` 。</span><span class="sxs-lookup"><span data-stu-id="d11ad-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="d11ad-114">如果沒有，請使用不同的語句將資料放入檔案中，或在適當模式中重新開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="d11ad-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="d11ad-115">如果您要寫入至唯讀檔案，請變更檔案的讀取/寫入狀態，或不要嘗試寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="d11ad-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="d11ad-116">使用 `My.Computer.FileSystem` 物件中可用的功能。</span><span class="sxs-lookup"><span data-stu-id="d11ad-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d11ad-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d11ad-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="d11ad-118">疑難排解：讀取和寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="d11ad-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
