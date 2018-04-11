---
title: 不正確的資料錄長度
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 747d62cb41ef841b4486e0c7108c37a86929683e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="bad-record-length"></a><span data-ttu-id="198dd-102">不正確的資料錄長度</span><span class="sxs-lookup"><span data-stu-id="198dd-102">Bad record length</span></span>
<span data-ttu-id="198dd-103">可能導致本錯誤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="198dd-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="198dd-104">記錄變數中指定的長度`FileGet`， `FileGetObject`，`FilePut`或`FilePutObject`陳述式與對應中指定的長度不同`FileOpen`陳述式。</span><span class="sxs-lookup"><span data-stu-id="198dd-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="198dd-105">中的變數`FilePut`或`FilePutObject`陳述式或包含可變長度字串。</span><span class="sxs-lookup"><span data-stu-id="198dd-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="198dd-106">中的變數`FilePut`或`FilePutObject`或包含`Variant`型別。</span><span class="sxs-lookup"><span data-stu-id="198dd-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="198dd-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="198dd-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="198dd-108">請確定記錄變數的型別定義使用者定義型別中的固定長度變數的大小總和為相同值中所述`FileOpen`陳述式的`Len`子句。</span><span class="sxs-lookup"><span data-stu-id="198dd-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="198dd-109">如果中的變數`FilePut`或`FilePutObject`陳述式或包含可變長度字串，請確定可變長度字串至少 2 個字元少於指定的資料錄長度`Len`子句`FileOpen`陳述式。</span><span class="sxs-lookup"><span data-stu-id="198dd-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="198dd-110">如果中的變數`FilePut`或`FilePutObject`或包含`Variant`請確定可變長度字串至少 4 個位元組中指定的記錄長度少於`Len`子句`FileOpen`陳述式。</span><span class="sxs-lookup"><span data-stu-id="198dd-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198dd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="198dd-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
