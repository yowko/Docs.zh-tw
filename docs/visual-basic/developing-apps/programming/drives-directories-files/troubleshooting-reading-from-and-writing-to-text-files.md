---
title: "疑難排解：讀取和寫入文字檔 (Visual Basic)"
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
- troubleshooting file I/O
- writing text to files, troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files, troubleshooting
- reading text files, troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: 10
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7f1d26df53445ee9711ebb2840071d2560c5380d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="dc406-102">疑難排解：讀取和寫入文字檔 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc406-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="dc406-103">本主題討論處理文字檔時所遇到的常見問題，並建議每個問題的處理方法。</span><span class="sxs-lookup"><span data-stu-id="dc406-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="dc406-104">常見問題</span><span class="sxs-lookup"><span data-stu-id="dc406-104">Common problems</span></span>  
 <span data-ttu-id="dc406-105">處理文字檔時所遇到的最常見問題包括安全性例外狀況、檔案編碼方式或無效路徑。</span><span class="sxs-lookup"><span data-stu-id="dc406-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="dc406-106">安全性例外狀況</span><span class="sxs-lookup"><span data-stu-id="dc406-106">Security exceptions</span></span>  
 <span data-ttu-id="dc406-107">發生安全性錯誤時，將會擲回 <xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="dc406-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="dc406-108">這通常是使用者缺乏必要權限所造成，而解決方法可能是新增權限，或處理隔離儲存空間中的檔案。</span><span class="sxs-lookup"><span data-stu-id="dc406-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="dc406-109">檔案編碼方式</span><span class="sxs-lookup"><span data-stu-id="dc406-109">File encodings</span></span>  
 <span data-ttu-id="dc406-110">檔案編碼方式，也稱為字元編碼方式，指定在處理文字時如何代表字元。</span><span class="sxs-lookup"><span data-stu-id="dc406-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="dc406-111">文字檔中的未預期字元可能是編碼方式不正確所造成。</span><span class="sxs-lookup"><span data-stu-id="dc406-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="dc406-112">針對大部分的檔案，就可以或無法處理的語言字元部分而言，可能會偏好使用某種編碼，但是通常偏好使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="dc406-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="dc406-113">如需詳細資訊，請參閱[檔案編碼方式](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)和 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="dc406-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="dc406-114">路徑不正確</span><span class="sxs-lookup"><span data-stu-id="dc406-114">Incorrect paths</span></span>  
 <span data-ttu-id="dc406-115">剖析檔案路徑時，特別是相對路徑，很容易就會提供錯誤資料。</span><span class="sxs-lookup"><span data-stu-id="dc406-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="dc406-116">確認您所提供的路徑正確，即可更正許多問題。</span><span class="sxs-lookup"><span data-stu-id="dc406-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="dc406-117">如需詳細資訊，請參閱[如何：剖析檔案路徑](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="dc406-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc406-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="dc406-118">See also</span></span>  
 <span data-ttu-id="dc406-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="dc406-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="dc406-120">[從檔案讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md) </span><span class="sxs-lookup"><span data-stu-id="dc406-120">[Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md) </span></span>  
 <span data-ttu-id="dc406-121">[寫入檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md) </span><span class="sxs-lookup"><span data-stu-id="dc406-121">[Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md) </span></span>  
 [<span data-ttu-id="dc406-122">使用 TextFieldParser 物件剖析文字檔</span><span class="sxs-lookup"><span data-stu-id="dc406-122">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)

