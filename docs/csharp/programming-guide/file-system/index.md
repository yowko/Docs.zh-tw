---
title: '檔案系統和登錄-c # 程式設計指南'
description: '觀看文章，示範如何使用 c # 和 .NET 來執行檔案、資料夾和登錄的基本作業。'
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 9e25058f5fb8ae49196c070dd426123e61a55e46
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301628"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="d996b-103">檔案系統和登錄（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="d996b-103">File system and the registry (C# Programming Guide)</span></span>

<span data-ttu-id="d996b-104">下列文章示範如何使用 c # 和 .NET 來執行檔案、資料夾和登錄的各種基本作業。</span><span class="sxs-lookup"><span data-stu-id="d996b-104">The following articles show how to use C# and .NET to perform various basic operations on files, folders, and the registry.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d996b-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="d996b-105">In this section</span></span>

|<span data-ttu-id="d996b-106">**標題**</span><span class="sxs-lookup"><span data-stu-id="d996b-106">**Title**</span></span>|<span data-ttu-id="d996b-107">**說明**</span><span class="sxs-lookup"><span data-stu-id="d996b-107">**Description**</span></span>|
|---------------|---------------------|
|[<span data-ttu-id="d996b-108">如何逐一查看目錄樹狀結構</span><span class="sxs-lookup"><span data-stu-id="d996b-108">How to iterate through a directory tree</span></span>](how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="d996b-109">示範如何手動逐一查看樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="d996b-109">Shows how to manually iterate through a directory tree.</span></span>|
|[<span data-ttu-id="d996b-110">如何取得有關檔案、資料夾和磁碟機的資訊</span><span class="sxs-lookup"><span data-stu-id="d996b-110">How to get information about files, folders, and drives</span></span>](how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="d996b-111">示範如何擷取有關檔案、資料夾和磁碟機的資訊，例如建立時間和大小。</span><span class="sxs-lookup"><span data-stu-id="d996b-111">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|
|[<span data-ttu-id="d996b-112">如何建立檔案或資料夾</span><span class="sxs-lookup"><span data-stu-id="d996b-112">How to create a file or folder</span></span>](how-to-create-a-file-or-folder.md)|<span data-ttu-id="d996b-113">示範如何建立新檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="d996b-113">Shows how to create a new file or folder.</span></span>|
|[<span data-ttu-id="d996b-114">如何複製、刪除和移動檔案和資料夾（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="d996b-114">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="d996b-115">示範如何複製、刪除和移動檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="d996b-115">Shows how to copy, delete and move files and folders.</span></span>|
|[<span data-ttu-id="d996b-116">如何提供檔案作業的進度對話方塊</span><span class="sxs-lookup"><span data-stu-id="d996b-116">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="d996b-117">示範如何針對特定檔案作業顯示標準 Windows 進度對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d996b-117">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|
|[<span data-ttu-id="d996b-118">如何寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="d996b-118">How to write to a text file</span></span>](how-to-write-to-a-text-file.md)|<span data-ttu-id="d996b-119">示範如何寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="d996b-119">Shows how to write to a text file.</span></span>|
|[<span data-ttu-id="d996b-120">如何從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="d996b-120">How to read from a text file</span></span>](how-to-read-from-a-text-file.md)|<span data-ttu-id="d996b-121">示範如何從文字檔讀取。</span><span class="sxs-lookup"><span data-stu-id="d996b-121">Shows how to read from a text file.</span></span>|
|[<span data-ttu-id="d996b-122">如何一次一行讀取文字檔</span><span class="sxs-lookup"><span data-stu-id="d996b-122">How to read a text file one line at a time</span></span>](how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="d996b-123">示範如何從檔案一次一行擷取文字。</span><span class="sxs-lookup"><span data-stu-id="d996b-123">Shows how to retrieve text from a file one line at a time.</span></span>|
|[<span data-ttu-id="d996b-124">如何在登錄中建立機碼</span><span class="sxs-lookup"><span data-stu-id="d996b-124">How to create a key in the registry</span></span>](how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="d996b-125">示範如何將機碼寫入至系統登錄。</span><span class="sxs-lookup"><span data-stu-id="d996b-125">Shows how to write a key to the system registry.</span></span>|

## <a name="related-sections"></a><span data-ttu-id="d996b-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="d996b-126">Related sections</span></span>

- [<span data-ttu-id="d996b-127">檔案和資料流程 i/o</span><span class="sxs-lookup"><span data-stu-id="d996b-127">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="d996b-128">如何複製、刪除和移動檔案和資料夾（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="d996b-128">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)
- [<span data-ttu-id="d996b-129">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d996b-129">C# Programming Guide</span></span>](../index.md)
- <xref:System.IO?displayProperty=nameWithType>
