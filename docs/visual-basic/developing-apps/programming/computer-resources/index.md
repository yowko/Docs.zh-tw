---
title: 存取電腦資源 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 5eb240b23d255987e96c58fefc7007c8030c6502
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524397"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="e941c-102">存取電腦資源 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e941c-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="e941c-103">`My.Computer` 物件是 `My` 中的三個中央物件之一，它們提供對資訊和常用功能的存取。</span><span class="sxs-lookup"><span data-stu-id="e941c-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="e941c-104">`My.Computer` 提供方法、屬性和事件來存取應用程式執行所在的電腦。</span><span class="sxs-lookup"><span data-stu-id="e941c-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="e941c-105">它的物件包括︰</span><span class="sxs-lookup"><span data-stu-id="e941c-105">Its objects include:</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <span data-ttu-id="e941c-106">剪貼簿(<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span><span class="sxs-lookup"><span data-stu-id="e941c-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
- <xref:Microsoft.VisualBasic.Devices.Clock>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
- <xref:Microsoft.VisualBasic.Devices.Keyboard>
- <xref:Microsoft.VisualBasic.Devices.Mouse>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <span data-ttu-id="e941c-107">登錄(<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span><span class="sxs-lookup"><span data-stu-id="e941c-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e941c-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="e941c-108">In this section</span></span>

[<span data-ttu-id="e941c-109">播放音效</span><span class="sxs-lookup"><span data-stu-id="e941c-109">Playing Sounds</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md)  
<span data-ttu-id="e941c-110">列出與 `My.Computer.Audio` 建立關聯的工作，例如在背景播放音效。</span><span class="sxs-lookup"><span data-stu-id="e941c-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

[<span data-ttu-id="e941c-111">在剪貼簿儲存和讀取資料</span><span class="sxs-lookup"><span data-stu-id="e941c-111">Storing Data to and Reading from the Clipboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)  
<span data-ttu-id="e941c-112">列出與 `My.Computer.Clipboard` 建立關聯的工作，例如從剪貼簿讀取資料或將資料寫入其中。</span><span class="sxs-lookup"><span data-stu-id="e941c-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

[<span data-ttu-id="e941c-113">取得電腦的相關資訊</span><span class="sxs-lookup"><span data-stu-id="e941c-113">Getting Information about the Computer</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md)  
<span data-ttu-id="e941c-114">列出與 `My.Computer.Info` 建立關聯的工作，例如判斷電腦的完整名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e941c-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

[<span data-ttu-id="e941c-115">存取鍵盤</span><span class="sxs-lookup"><span data-stu-id="e941c-115">Accessing the Keyboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)  
<span data-ttu-id="e941c-116">列出與 `My.Computer.Keyboard` 建立關聯的工作，例如判斷是否開啟 CAPS LOCK。</span><span class="sxs-lookup"><span data-stu-id="e941c-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

[<span data-ttu-id="e941c-117">存取滑鼠</span><span class="sxs-lookup"><span data-stu-id="e941c-117">Accessing the Mouse</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md)  
<span data-ttu-id="e941c-118">列出與 `My.Computer.Mouse` 建立關聯的工作，例如判斷是否有滑鼠。</span><span class="sxs-lookup"><span data-stu-id="e941c-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

[<span data-ttu-id="e941c-119">執行網路作業</span><span class="sxs-lookup"><span data-stu-id="e941c-119">Performing Network Operations</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md)  
<span data-ttu-id="e941c-120">列出與 `My.Computer.Network` 建立關聯的工作，例如上傳或下載檔案。</span><span class="sxs-lookup"><span data-stu-id="e941c-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

[<span data-ttu-id="e941c-121">存取電腦的連接埠</span><span class="sxs-lookup"><span data-stu-id="e941c-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)  
<span data-ttu-id="e941c-122">列出與 `My.Computer.Ports` 建立關聯的工作，例如顯示可用序列埠或將字串傳送至序列埠。</span><span class="sxs-lookup"><span data-stu-id="e941c-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

[<span data-ttu-id="e941c-123">讀取和寫入登錄</span><span class="sxs-lookup"><span data-stu-id="e941c-123">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
<span data-ttu-id="e941c-124">列出與 `My.Computer.Registry` 建立關聯的工作，例如從登錄機碼讀取資料或將資料寫入其中。</span><span class="sxs-lookup"><span data-stu-id="e941c-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
