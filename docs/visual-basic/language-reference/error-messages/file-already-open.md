---
title: 檔案已經開啟
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: ce8f8bf96d7355e45b2df82e8a131472c2ed2367
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162748"
---
# <a name="file-already-open"></a><span data-ttu-id="cbaae-102">檔案已經開啟</span><span class="sxs-lookup"><span data-stu-id="cbaae-102">File already open</span></span>

<span data-ttu-id="cbaae-103">有時候必須先關閉檔案，才能 `FileOpen` 進行其他或其他操作。</span><span class="sxs-lookup"><span data-stu-id="cbaae-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="cbaae-104">可能導致本錯誤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="cbaae-104">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="cbaae-105">已針對已開啟的檔案執行連續輸出模式作業 `FileOpen`</span><span class="sxs-lookup"><span data-stu-id="cbaae-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>

- <span data-ttu-id="cbaae-106">語句指的是開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="cbaae-106">A statement refers to an open file.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="cbaae-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cbaae-107">To correct this error</span></span>

- <span data-ttu-id="cbaae-108">請先關閉檔案，再執行語句。</span><span class="sxs-lookup"><span data-stu-id="cbaae-108">Close the file before executing the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbaae-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbaae-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
