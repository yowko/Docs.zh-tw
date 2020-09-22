---
title: 不正確的資料錄長度
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 6967015572b2567f52697f7ddcb1ff594013a2c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869255"
---
# <a name="bad-record-length"></a><span data-ttu-id="4dc97-102">不正確的資料錄長度</span><span class="sxs-lookup"><span data-stu-id="4dc97-102">Bad record length</span></span>

<span data-ttu-id="4dc97-103">可能導致本錯誤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="4dc97-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="4dc97-104">、或語句中指定的記錄變數長度 `FileGet` ， `FileGetObject` `FilePut` `FilePutObject` 與對應的語句中所指定的長度不同 `FileOpen` 。</span><span class="sxs-lookup"><span data-stu-id="4dc97-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
- <span data-ttu-id="4dc97-105">或語句中的 `FilePut` 變數 `FilePutObject` 為或包含可變長度的字串。</span><span class="sxs-lookup"><span data-stu-id="4dc97-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
- <span data-ttu-id="4dc97-106">或中的變數 `FilePut` `FilePutObject` 為或包含 `Variant` 類型。</span><span class="sxs-lookup"><span data-stu-id="4dc97-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4dc97-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4dc97-107">To correct this error</span></span>  
  
1. <span data-ttu-id="4dc97-108">請確定定義記錄變數型別的使用者定義型別中的固定長度變數大小總和，與語句子句中所述的值相同 `FileOpen` `Len` 。</span><span class="sxs-lookup"><span data-stu-id="4dc97-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2. <span data-ttu-id="4dc97-109">如果或語句中的 `FilePut` 變數 `FilePutObject` 為或包含可變長度的字串，請確定變數長度字串至少為2個字元，且小於語句的子句中指定的記錄長度 `Len` `FileOpen` 。</span><span class="sxs-lookup"><span data-stu-id="4dc97-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3. <span data-ttu-id="4dc97-110">如果或中的變數 `FilePut` `FilePutObject` 為或包含， `Variant` 請確定可變長度字串的長度至少為4個位元組，且小於語句的子句中指定的記錄長度 `Len` `FileOpen` 。</span><span class="sxs-lookup"><span data-stu-id="4dc97-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc97-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dc97-111">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
