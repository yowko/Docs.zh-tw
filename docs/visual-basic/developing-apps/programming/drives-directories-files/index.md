---
title: 處理磁碟機、目錄和檔案
ms.date: 07/20/2015
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
ms.openlocfilehash: b69c65621f3849b07bd31f569fc4ae9fe04b50a6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411560"
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="d5ecf-102">處理磁碟機、目錄和檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5ecf-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>

<span data-ttu-id="d5ecf-103">您可以使用 Visual Basic，利用 `My.Computer.FileSystem` 物件來處理磁碟機、資料夾和檔案，這個物件提供更佳效能，而且比 `FileOpen` 和 `Write` 函式等傳統方法更容易使用 (不過仍然可供使用)。</span><span class="sxs-lookup"><span data-stu-id="d5ecf-103">You can use Visual Basic to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="d5ecf-104">下列各節詳細討論這些方法。</span><span class="sxs-lookup"><span data-stu-id="d5ecf-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5ecf-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="d5ecf-105">In This Section</span></span>  

 [<span data-ttu-id="d5ecf-106">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="d5ecf-106">File Access with Visual Basic</span></span>](file-access.md)  
 <span data-ttu-id="d5ecf-107">說明如何使用 `My.Computer.FileSystem` 物件來處理檔案、磁碟機和資料夾。</span><span class="sxs-lookup"><span data-stu-id="d5ecf-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="d5ecf-108">.NET Framework 檔案 I/O 和檔案系統基本概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5ecf-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="d5ecf-109">提供 .NET Framework 中檔案 I/O 概念的概觀，包括資料流、隔離儲存區、檔案事件、檔案屬性和檔案存取。</span><span class="sxs-lookup"><span data-stu-id="d5ecf-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="d5ecf-110">逐步解說：使用 .NET Framework 方法管理檔案</span><span class="sxs-lookup"><span data-stu-id="d5ecf-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="d5ecf-111">示範如何使用 .NET Framework 來處理檔案與資料夾。</span><span class="sxs-lookup"><span data-stu-id="d5ecf-111">Demonstrates how to use the .NET Framework to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="d5ecf-112">逐步解說：在 Visual Basic 中管理檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="d5ecf-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="d5ecf-113">示範如何使用 `My.Computer.FileSystem` 物件來管理檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="d5ecf-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d5ecf-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="d5ecf-114">Related Sections</span></span>  

 [<span data-ttu-id="d5ecf-115">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="d5ecf-115">Program Structure and Code Conventions</span></span>](../../../programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="d5ecf-116">提供程式實體結構及外觀的方針。</span><span class="sxs-lookup"><span data-stu-id="d5ecf-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="d5ecf-117">`My.Computer.FileSystem` 物件及其成員的參考文件。</span><span class="sxs-lookup"><span data-stu-id="d5ecf-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
