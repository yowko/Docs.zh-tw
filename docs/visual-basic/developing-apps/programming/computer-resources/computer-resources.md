---
title: "存取電腦資源 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20c9d23570ec986598ad697f559aaf3a3153a8a0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="77741-102">存取電腦資源 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77741-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="77741-103">`My.Computer` 物件是 `My` 中的三個中央物件之一，它們提供對資訊和常用功能的存取。</span><span class="sxs-lookup"><span data-stu-id="77741-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="77741-104">`My.Computer` 提供方法、屬性和事件來存取應用程式執行所在的電腦。</span><span class="sxs-lookup"><span data-stu-id="77741-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="77741-105">它的物件包括︰</span><span class="sxs-lookup"><span data-stu-id="77741-105">Its objects include:</span></span>  
  
-   <xref:Microsoft.VisualBasic.Devices.Audio>
-   <span data-ttu-id="77741-106">剪貼簿(<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span><span class="sxs-lookup"><span data-stu-id="77741-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
-   <xref:Microsoft.VisualBasic.Devices.Clock>
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem>
-   <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
-   <xref:Microsoft.VisualBasic.Devices.Keyboard>
-   <xref:Microsoft.VisualBasic.Devices.Mouse>
-   <xref:Microsoft.VisualBasic.Devices.Network>
-   <xref:Microsoft.VisualBasic.Devices.Ports>
-   <span data-ttu-id="77741-107">登錄(<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span><span class="sxs-lookup"><span data-stu-id="77741-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="77741-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="77741-108">In this section</span></span>

<span data-ttu-id="77741-109">[播放音效](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md) </span><span class="sxs-lookup"><span data-stu-id="77741-109">[Playing Sounds](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md) </span></span>  
<span data-ttu-id="77741-110">列出與 `My.Computer.Audio` 建立關聯的工作，例如在背景播放音效。</span><span class="sxs-lookup"><span data-stu-id="77741-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

<span data-ttu-id="77741-111">[在剪貼簿儲存和讀取資料](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md) </span><span class="sxs-lookup"><span data-stu-id="77741-111">[Storing Data to and Reading from the Clipboard](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md) </span></span>  
<span data-ttu-id="77741-112">列出與 `My.Computer.Clipboard` 建立關聯的工作，例如從剪貼簿讀取資料或將資料寫入其中。</span><span class="sxs-lookup"><span data-stu-id="77741-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

<span data-ttu-id="77741-113">[取得電腦的相關資訊](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md) </span><span class="sxs-lookup"><span data-stu-id="77741-113">[Getting Information about the Computer](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md) </span></span>  
<span data-ttu-id="77741-114">列出與 `My.Computer.Info` 建立關聯的工作，例如判斷電腦的完整名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="77741-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

<span data-ttu-id="77741-115">[存取鍵盤](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="77741-115">[Accessing the Keyboard](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md) </span></span>  
<span data-ttu-id="77741-116">列出與 `My.Computer.Keyboard` 建立關聯的工作，例如判斷是否開啟 CAPS LOCK。</span><span class="sxs-lookup"><span data-stu-id="77741-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

<span data-ttu-id="77741-117">[存取滑鼠](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md) </span><span class="sxs-lookup"><span data-stu-id="77741-117">[Accessing the Mouse](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md) </span></span>  
<span data-ttu-id="77741-118">列出與 `My.Computer.Mouse` 建立關聯的工作，例如判斷是否有滑鼠。</span><span class="sxs-lookup"><span data-stu-id="77741-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

<span data-ttu-id="77741-119">[執行網路作業](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md) </span><span class="sxs-lookup"><span data-stu-id="77741-119">[Performing Network Operations](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md) </span></span>  
<span data-ttu-id="77741-120">列出與 `My.Computer.Network` 建立關聯的工作，例如上傳或下載檔案。</span><span class="sxs-lookup"><span data-stu-id="77741-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

<span data-ttu-id="77741-121">[存取電腦的連接埠](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md) </span><span class="sxs-lookup"><span data-stu-id="77741-121">[Accessing the Computer's Ports](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md) </span></span>  
<span data-ttu-id="77741-122">列出與 `My.Computer.Ports` 建立關聯的工作，例如顯示可用序列埠或將字串傳送至序列埠。</span><span class="sxs-lookup"><span data-stu-id="77741-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

<span data-ttu-id="77741-123">[讀取和寫入登錄](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="77741-123">[Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span></span>  
<span data-ttu-id="77741-124">列出與 `My.Computer.Registry` 建立關聯的工作，例如從登錄機碼讀取資料或將資料寫入其中。</span><span class="sxs-lookup"><span data-stu-id="77741-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
