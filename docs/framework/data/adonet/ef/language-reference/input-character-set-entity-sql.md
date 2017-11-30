---
title: "輸入字元集 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 691f29a04b1b1f997be501330ec887d6815d7531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="input-character-set-entity-sql"></a><span data-ttu-id="29b96-102">輸入字元集 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="29b96-102">Input Character Set (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="29b96-103"> 接受以 UTF-16 編碼的 UNICODE 字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-103"> accepts UNICODE characters encoded in UTF-16.</span></span>  
  
 <span data-ttu-id="29b96-104">字串常值 (String Literal) 可包含以單引號括住的任何 UTF-16 字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-104">String literals can contain any UTF-16 character enclosed in single quotes.</span></span> <span data-ttu-id="29b96-105">例如，N'文字列リテラル'。</span><span class="sxs-lookup"><span data-stu-id="29b96-105">For example, N'文字列リテラル'.</span></span> <span data-ttu-id="29b96-106">當比較字串常值時，會使用原始的 UTF-16 值。</span><span class="sxs-lookup"><span data-stu-id="29b96-106">When string literals are compared, the original UTF-16 values are used.</span></span> <span data-ttu-id="29b96-107">例如，N'ABC' 在日文字碼頁和拉丁文字碼頁中是不同的。</span><span class="sxs-lookup"><span data-stu-id="29b96-107">For example, N'ABC' is different in Japanese and Latin codepages.</span></span>  
  
 <span data-ttu-id="29b96-108">註解可包含任何 UTF-16 字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-108">Comments can contain any UTF-16 character.</span></span>  
  
 <span data-ttu-id="29b96-109">逸出的識別碼可包含以方括弧括住的任何 UTF-16 字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-109">Escaped identifiers can contain any UTF-16 character enclosed in square brackets.</span></span> <span data-ttu-id="29b96-110">例如，[エスケープされた識別子]。</span><span class="sxs-lookup"><span data-stu-id="29b96-110">For example, [エスケープされた識別子].</span></span> <span data-ttu-id="29b96-111">UTF-16 逸出識別碼的比較是不區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="29b96-111">The comparison of UTF-16 escaped identifiers is case insensitive.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="29b96-112"> 會將看起來一樣卻來自不同字碼頁的字母版本視為不同字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-112"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="29b96-113">例如，如果對應的字元來自相同的字碼頁，則 [ABC] 相當於 [abc]。</span><span class="sxs-lookup"><span data-stu-id="29b96-113">For example, [ABC] is equivalent to [abc] if the corresponding characters are from the same code page.</span></span> <span data-ttu-id="29b96-114">然而，如果相同的兩個識別碼來自不同的字碼頁，則不相等。</span><span class="sxs-lookup"><span data-stu-id="29b96-114">However, if the same two identifiers are from different code pages, they are not equivalent.</span></span>  
  
 <span data-ttu-id="29b96-115">空白區是任何 UTF-16 空白字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-115">White space is any UTF-16 white space character.</span></span>  
  
 <span data-ttu-id="29b96-116">新行 (Newline) 是任何標準化的 UTF-16 新行字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-116">A newline is any normalized UTF-16 newline character.</span></span> <span data-ttu-id="29b96-117">例如，'\n' 和 '\r\n' 會視為新行字元，但是 '\r' 不是新行字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-117">For example, '\n' and '\r\n' are considered newline characters, but '\r' is not a newline character.</span></span>  
  
 <span data-ttu-id="29b96-118">關鍵字、運算式和標點符號可以是任何標準化成拉丁文的 UTF-16 字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-118">Keywords, expressions, and punctuation can be any UTF-16 character that normalizes to Latin.</span></span> <span data-ttu-id="29b96-119">例如，SELECT 在日文字碼頁中是一個有效的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="29b96-119">For example, SELECT in a Japanese codepage is a valid keyword.</span></span>  
  
 <span data-ttu-id="29b96-120">關鍵字、運算式和標點符號只能是拉丁文字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-120">Keywords, expressions, and punctuation can only be Latin characters.</span></span> <span data-ttu-id="29b96-121">`SELECT` 在日文字碼頁中不是關鍵字。</span><span class="sxs-lookup"><span data-stu-id="29b96-121">`SELECT` in a Japanese codepage is not a keyword.</span></span> <span data-ttu-id="29b96-122">這裡未以括號括住的 +、-、*、/、=、(、)、‘、[、] 和任何其他語言建構只能是拉丁字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-122">+, -, *, /, =, (, ), ‘, [, ] and any other language construct not quoted here can only be Latin characters.</span></span>  
  
 <span data-ttu-id="29b96-123">簡單識別碼只能是拉丁字元。</span><span class="sxs-lookup"><span data-stu-id="29b96-123">Simple identifiers can only be Latin characters.</span></span> <span data-ttu-id="29b96-124">如此可避免比較期間的模稜兩可 (Ambiguity)，因為會比較原始值。</span><span class="sxs-lookup"><span data-stu-id="29b96-124">This avoids ambiguity during comparison, because original values are compared.</span></span> <span data-ttu-id="29b96-125">例如，ABC 在日文字碼頁和拉丁文字碼頁中是不同的。</span><span class="sxs-lookup"><span data-stu-id="29b96-125">For example, ABC would be different in in Japanese and Latin codepages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b96-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29b96-126">See Also</span></span>  
 [<span data-ttu-id="29b96-127">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="29b96-127">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
