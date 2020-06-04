---
title: 不正確的檔案模式
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409865"
---
# <a name="bad-file-mode"></a><span data-ttu-id="4f2e4-102">不正確的檔案模式</span><span class="sxs-lookup"><span data-stu-id="4f2e4-102">Bad file mode</span></span>
<span data-ttu-id="4f2e4-103">用於操作檔案內容的語句，必須適合用來開啟檔案的模式。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="4f2e4-104">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="4f2e4-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="4f2e4-105">`FilePutObject`或 `FileGetObject` 語句指定了連續的檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="4f2e4-106">`Print`語句會指定針對或以外的存取模式開啟的檔案 `Output` `Append` 。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="4f2e4-107">`Input`語句指定針對存取模式開啟的檔案，而非`Input`</span><span class="sxs-lookup"><span data-stu-id="4f2e4-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="4f2e4-108">嘗試寫入唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4f2e4-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4f2e4-109">To correct this error</span></span>  
  
- <span data-ttu-id="4f2e4-110">請確定 `FilePutObject` 和 `FileGetObject` 只會參考開啟 `Random` 或存取的檔案 `Binary` 。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="4f2e4-111">請確定 `Print` 指定針對 `Output` 或存取模式開啟的檔案 `Append` 。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="4f2e4-112">如果不是，請使用不同的語句將資料放在檔案中，或在適當的模式中重新開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="4f2e4-113">請確定 `Input` 指定為開啟的檔案 `Input` 。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="4f2e4-114">如果不是，請使用不同的語句將資料放在檔案中，或在適當的模式中重新開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="4f2e4-115">如果您要寫入唯讀檔案，請變更檔案的讀取/寫入狀態，或不要嘗試寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="4f2e4-116">使用 `My.Computer.FileSystem` 物件中可用的功能。</span><span class="sxs-lookup"><span data-stu-id="4f2e4-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f2e4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f2e4-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="4f2e4-118">疑難排解：讀取和寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="4f2e4-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
