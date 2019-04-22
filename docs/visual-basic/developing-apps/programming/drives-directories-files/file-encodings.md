---
title: 檔案編碼方式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: c22e8046a8b88890f25bc6b671825eb6d68ec6b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813999"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="95e32-102">檔案編碼方式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95e32-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="95e32-103">檔案編碼方式，也稱為字元編碼方式，指定在處理文字時如何代表字元。</span><span class="sxs-lookup"><span data-stu-id="95e32-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="95e32-104">就可以或無法處理的語言字元部分而言，可能會偏好使用某種編碼，但是通常偏好使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="95e32-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="95e32-105">讀取或寫入檔案時，不相符的檔案編碼方式可能會導致例外狀況或不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="95e32-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="95e32-106">編碼方式的類型</span><span class="sxs-lookup"><span data-stu-id="95e32-106">Types of Encodings</span></span>  
 <span data-ttu-id="95e32-107">使用檔案時，Unicode 是慣用的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="95e32-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="95e32-108">Unicode 是全球字元編碼標準，可使用 16 位元字碼值代表現代計算中所使用的所有字元 (包括發行中所使用的技術符號和特殊字元)。</span><span class="sxs-lookup"><span data-stu-id="95e32-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="95e32-109">先前的字元編碼標準包含傳統字元集 (例如使用 8 位元字碼值或 8 位元值組合的 Windows ANSI 字元集)，以代表特定語言或地區中所使用的字元。</span><span class="sxs-lookup"><span data-stu-id="95e32-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="95e32-110">編碼類別</span><span class="sxs-lookup"><span data-stu-id="95e32-110">Encoding Class</span></span>  
 <span data-ttu-id="95e32-111"><xref:System.Text.Encoding> 類別表示字元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="95e32-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="95e32-112">此表列出可用的編碼方式類型，並描述每個編碼方式。</span><span class="sxs-lookup"><span data-stu-id="95e32-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="95e32-113">名稱</span><span class="sxs-lookup"><span data-stu-id="95e32-113">Name</span></span>|<span data-ttu-id="95e32-114">說明</span><span class="sxs-lookup"><span data-stu-id="95e32-114">Description</span></span>|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="95e32-115">代表 Unicode 字元的 ASCII 字元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="95e32-115">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="95e32-116">代表 Unicode 字元的 UTF-16 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="95e32-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="95e32-117">代表 Unicode 字元的 UTF-32 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="95e32-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="95e32-118">代表 Unicode 字元的 UTF-7 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="95e32-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="95e32-119">代表 Unicode 字元的 UTF-8 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="95e32-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95e32-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95e32-120">See also</span></span>

- [<span data-ttu-id="95e32-121">從檔案讀取</span><span class="sxs-lookup"><span data-stu-id="95e32-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="95e32-122">寫入檔案</span><span class="sxs-lookup"><span data-stu-id="95e32-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
