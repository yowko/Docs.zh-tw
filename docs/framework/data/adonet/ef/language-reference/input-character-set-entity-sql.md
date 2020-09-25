---
title: 輸入字元集 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: 94615a8f4aec51347f451d6f6a53b9d5b459a336
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203653"
---
# <a name="input-character-set-entity-sql"></a><span data-ttu-id="02f47-102">輸入字元集 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="02f47-102">Input Character Set (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="02f47-103">接受以 UTF-16 編碼的 UNICODE 字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-103">accepts UNICODE characters encoded in UTF-16.</span></span>  
  
 <span data-ttu-id="02f47-104">字串常值 (String Literal) 可包含以單引號括住的任何 UTF-16 字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-104">String literals can contain any UTF-16 character enclosed in single quotes.</span></span> <span data-ttu-id="02f47-105">例如，N'文字列リテラル'。</span><span class="sxs-lookup"><span data-stu-id="02f47-105">For example, N'文字列リテラル'.</span></span> <span data-ttu-id="02f47-106">當比較字串常值時，會使用原始的 UTF-16 值。</span><span class="sxs-lookup"><span data-stu-id="02f47-106">When string literals are compared, the original UTF-16 values are used.</span></span> <span data-ttu-id="02f47-107">例如，N'ABC' 在日文字碼頁和拉丁文字碼頁中是不同的。</span><span class="sxs-lookup"><span data-stu-id="02f47-107">For example, N'ABC' is different in Japanese and Latin codepages.</span></span>  
  
 <span data-ttu-id="02f47-108">註解可包含任何 UTF-16 字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-108">Comments can contain any UTF-16 character.</span></span>  
  
 <span data-ttu-id="02f47-109">逸出的識別碼可包含以方括弧括住的任何 UTF-16 字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-109">Escaped identifiers can contain any UTF-16 character enclosed in square brackets.</span></span> <span data-ttu-id="02f47-110">例如，[エスケープされた識別子]。</span><span class="sxs-lookup"><span data-stu-id="02f47-110">For example, [エスケープされた識別子].</span></span> <span data-ttu-id="02f47-111">UTF-16 逸出識別碼的比較是不區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="02f47-111">The comparison of UTF-16 escaped identifiers is case insensitive.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="02f47-112">會將看起來一樣卻來自不同字碼頁的字母版本視為不同字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-112">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="02f47-113">例如，如果對應的字元來自相同的字碼頁，則 [ABC] 相當於 [abc]。</span><span class="sxs-lookup"><span data-stu-id="02f47-113">For example, [ABC] is equivalent to [abc] if the corresponding characters are from the same code page.</span></span> <span data-ttu-id="02f47-114">然而，如果相同的兩個識別碼來自不同的字碼頁，則不相等。</span><span class="sxs-lookup"><span data-stu-id="02f47-114">However, if the same two identifiers are from different code pages, they are not equivalent.</span></span>  
  
 <span data-ttu-id="02f47-115">空白區是任何 UTF-16 空白字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-115">White space is any UTF-16 white space character.</span></span>  
  
 <span data-ttu-id="02f47-116">新行 (Newline) 是任何標準化的 UTF-16 新行字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-116">A newline is any normalized UTF-16 newline character.</span></span> <span data-ttu-id="02f47-117">例如，'\n' 和 '\r\n' 會視為新行字元，但是 '\r' 不是新行字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-117">For example, '\n' and '\r\n' are considered newline characters, but '\r' is not a newline character.</span></span>  
  
 <span data-ttu-id="02f47-118">關鍵字、運算式和標點符號可以是任何標準化成拉丁文的 UTF-16 字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-118">Keywords, expressions, and punctuation can be any UTF-16 character that normalizes to Latin.</span></span> <span data-ttu-id="02f47-119">例如，SELECT 在日文字碼頁中是一個有效的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="02f47-119">For example, SELECT in a Japanese codepage is a valid keyword.</span></span>  
  
 <span data-ttu-id="02f47-120">關鍵字、運算式和標點符號只能是拉丁文字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-120">Keywords, expressions, and punctuation can only be Latin characters.</span></span> <span data-ttu-id="02f47-121">`SELECT` 在日文字碼頁中不是關鍵字。</span><span class="sxs-lookup"><span data-stu-id="02f47-121">`SELECT` in a Japanese codepage is not a keyword.</span></span> <span data-ttu-id="02f47-122">+、-、 \* 、/、=、 (、) 、'、[、] 和任何其他未加上引號的語言結構，只能是拉丁字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-122">+, -, \*, /, =, (, ), ‘, [, ] and any other language construct not quoted here can only be Latin characters.</span></span>  
  
 <span data-ttu-id="02f47-123">簡單識別碼只能是拉丁字元。</span><span class="sxs-lookup"><span data-stu-id="02f47-123">Simple identifiers can only be Latin characters.</span></span> <span data-ttu-id="02f47-124">如此可避免比較期間的模稜兩可 (Ambiguity)，因為會比較原始值。</span><span class="sxs-lookup"><span data-stu-id="02f47-124">This avoids ambiguity during comparison, because original values are compared.</span></span> <span data-ttu-id="02f47-125">例如，在日文和拉丁字碼頁中，ABC 會有所不同。</span><span class="sxs-lookup"><span data-stu-id="02f47-125">For example, ABC would be different in Japanese and Latin codepages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f47-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02f47-126">See also</span></span>

- [<span data-ttu-id="02f47-127">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="02f47-127">Entity SQL Overview</span></span>](entity-sql-overview.md)
