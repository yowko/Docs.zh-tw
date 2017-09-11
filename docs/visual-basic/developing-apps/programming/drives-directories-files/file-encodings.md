---
title: "檔案編碼方式 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- character encodings
- files, encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d59312951429780990e9cc048e3ad0671b81d8ae
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="24d8b-102">檔案編碼方式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24d8b-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="24d8b-103">檔案編碼方式，也稱為字元編碼方式，指定在處理文字時如何代表字元。</span><span class="sxs-lookup"><span data-stu-id="24d8b-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="24d8b-104">就可以或無法處理的語言字元部分而言，可能會偏好使用某種編碼，但是通常偏好使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="24d8b-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="24d8b-105">讀取或寫入檔案時，不相符的檔案編碼方式可能會導致例外狀況或不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="24d8b-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="24d8b-106">編碼方式的類型</span><span class="sxs-lookup"><span data-stu-id="24d8b-106">Types of Encodings</span></span>  
 <span data-ttu-id="24d8b-107">使用檔案時，Unicode 是慣用的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="24d8b-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="24d8b-108">Unicode 是全球字元編碼標準，可使用 16 位元字碼值代表現代計算中所使用的所有字元 (包括發行中所使用的技術符號和特殊字元)。</span><span class="sxs-lookup"><span data-stu-id="24d8b-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="24d8b-109">先前的字元編碼標準包含傳統字元集 (例如使用 8 位元字碼值或 8 位元值組合的 Windows ANSI 字元集)，以代表特定語言或地區中所使用的字元。</span><span class="sxs-lookup"><span data-stu-id="24d8b-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="24d8b-110">編碼類別</span><span class="sxs-lookup"><span data-stu-id="24d8b-110">Encoding Class</span></span>  
 <span data-ttu-id="24d8b-111"><xref:System.Text.Encoding> 類別代表字元編碼。</span><span class="sxs-lookup"><span data-stu-id="24d8b-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="24d8b-112">此表列出可用的編碼方式類型，並描述每個編碼方式。</span><span class="sxs-lookup"><span data-stu-id="24d8b-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="24d8b-113">名稱</span><span class="sxs-lookup"><span data-stu-id="24d8b-113">Name</span></span>|<span data-ttu-id="24d8b-114">說明</span><span class="sxs-lookup"><span data-stu-id="24d8b-114">Description</span></span>|
|---|---|    
|<span data-ttu-id="24d8b-115"><xref:System.Text.ASCIIEncoding></span><span class="sxs-lookup"><span data-stu-id="24d8b-115"><xref:System.Text.ASCIIEncoding></span></span>|<span data-ttu-id="24d8b-116">代表 Unicode 字元的 ASCII 字元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="24d8b-116">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<span data-ttu-id="24d8b-117"><xref:System.Text.UnicodeEncoding></span><span class="sxs-lookup"><span data-stu-id="24d8b-117"><xref:System.Text.UnicodeEncoding></span></span>|<span data-ttu-id="24d8b-118">代表 Unicode 字元的 UTF-16 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="24d8b-118">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<span data-ttu-id="24d8b-119"><xref:System.Text.UTF32Encoding></span><span class="sxs-lookup"><span data-stu-id="24d8b-119"><xref:System.Text.UTF32Encoding></span></span>|<span data-ttu-id="24d8b-120">代表 Unicode 字元的 UTF-32 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="24d8b-120">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<span data-ttu-id="24d8b-121"><xref:System.Text.UTF7Encoding></span><span class="sxs-lookup"><span data-stu-id="24d8b-121"><xref:System.Text.UTF7Encoding></span></span>|<span data-ttu-id="24d8b-122">代表 Unicode 字元的 UTF-7 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="24d8b-122">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<span data-ttu-id="24d8b-123"><xref:System.Text.UTF8Encoding></span><span class="sxs-lookup"><span data-stu-id="24d8b-123"><xref:System.Text.UTF8Encoding></span></span>|<span data-ttu-id="24d8b-124">代表 Unicode 字元的 UTF-8 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="24d8b-124">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24d8b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24d8b-125">See Also</span></span>  
 <span data-ttu-id="24d8b-126">[從檔案讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md) </span><span class="sxs-lookup"><span data-stu-id="24d8b-126">[Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md) </span></span>  
<span data-ttu-id="24d8b-127"> [寫入檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)</span><span class="sxs-lookup"><span data-stu-id="24d8b-127"> [Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)</span></span>
