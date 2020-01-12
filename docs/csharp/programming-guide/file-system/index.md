---
title: 檔案系統和登錄程式C#設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: f160df456f1a3437e11de2d3660d158ae4d4bb67
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900569"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="f1bb0-102">檔案系統和登錄（C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="f1bb0-102">File system and the registry (C# Programming Guide)</span></span>

<span data-ttu-id="f1bb0-103">下列文章示範如何使用C#和 .net，在檔案、資料夾和登錄上執行各種基本作業。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-103">The following articles show how to use C# and .NET to perform various basic operations on files, folders, and the registry.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f1bb0-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="f1bb0-104">In this section</span></span>

|<span data-ttu-id="f1bb0-105">**標題**</span><span class="sxs-lookup"><span data-stu-id="f1bb0-105">**Title**</span></span>|<span data-ttu-id="f1bb0-106">**描述**</span><span class="sxs-lookup"><span data-stu-id="f1bb0-106">**Description**</span></span>|
|---------------|---------------------|
|[<span data-ttu-id="f1bb0-107">如何逐一查看目錄樹狀結構</span><span class="sxs-lookup"><span data-stu-id="f1bb0-107">How to iterate through a directory tree</span></span>](how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="f1bb0-108">示範如何手動逐一查看樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-108">Shows how to manually iterate through a directory tree.</span></span>|
|[<span data-ttu-id="f1bb0-109">如何取得有關檔案、資料夾和磁片磁碟機的資訊</span><span class="sxs-lookup"><span data-stu-id="f1bb0-109">How to get information about files, folders, and drives</span></span>](how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="f1bb0-110">示範如何擷取有關檔案、資料夾和磁碟機的資訊，例如建立時間和大小。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|
|[<span data-ttu-id="f1bb0-111">如何建立檔案或資料夾</span><span class="sxs-lookup"><span data-stu-id="f1bb0-111">How to create a file or folder</span></span>](how-to-create-a-file-or-folder.md)|<span data-ttu-id="f1bb0-112">示範如何建立新檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-112">Shows how to create a new file or folder.</span></span>|
|[<span data-ttu-id="f1bb0-113">如何複製、刪除和移動檔案和資料夾（C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="f1bb0-113">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="f1bb0-114">示範如何複製、刪除和移動檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-114">Shows how to copy, delete and move files and folders.</span></span>|
|[<span data-ttu-id="f1bb0-115">如何提供檔案作業的進度對話方塊</span><span class="sxs-lookup"><span data-stu-id="f1bb0-115">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="f1bb0-116">示範如何針對特定檔案作業顯示標準 Windows 進度對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|
|[<span data-ttu-id="f1bb0-117">如何寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="f1bb0-117">How to write to a text file</span></span>](how-to-write-to-a-text-file.md)|<span data-ttu-id="f1bb0-118">示範如何寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-118">Shows how to write to a text file.</span></span>|
|[<span data-ttu-id="f1bb0-119">如何從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="f1bb0-119">How to read from a text file</span></span>](how-to-read-from-a-text-file.md)|<span data-ttu-id="f1bb0-120">示範如何從文字檔讀取。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-120">Shows how to read from a text file.</span></span>|
|[<span data-ttu-id="f1bb0-121">如何一次一行讀取文字檔</span><span class="sxs-lookup"><span data-stu-id="f1bb0-121">How to read a text file one line at a time</span></span>](how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="f1bb0-122">示範如何從檔案一次一行擷取文字。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-122">Shows how to retrieve text from a file one line at a time.</span></span>|
|[<span data-ttu-id="f1bb0-123">如何在登錄中建立機碼</span><span class="sxs-lookup"><span data-stu-id="f1bb0-123">How to create a key in the registry</span></span>](how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="f1bb0-124">示範如何將機碼寫入至系統登錄。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-124">Shows how to write a key to the system registry.</span></span>|

## <a name="related-sections"></a><span data-ttu-id="f1bb0-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="f1bb0-125">Related sections</span></span>

- [<span data-ttu-id="f1bb0-126">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="f1bb0-126">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="f1bb0-127">如何複製、刪除和移動檔案和資料夾（C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="f1bb0-127">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)
- [<span data-ttu-id="f1bb0-128">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f1bb0-128">C# Programming Guide</span></span>](../index.md)
- <xref:System.IO?displayProperty=nameWithType>
