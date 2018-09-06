---
title: Windows Form 中的使用者輸入
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], using in Windows Forms
- Windows Forms, user input
- mouse input [Windows Forms], using in Windows Forms
- keyboards [Windows Forms], keyboard input
ms.assetid: 1486075f-1e06-4c9e-82c6-f948331db6d6
ms.openlocfilehash: fef51f57dd3c14c91572041a72c805823d6019a3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740931"
---
# <a name="user-input-in-windows-forms"></a><span data-ttu-id="eed55-102">Windows Form 中的使用者輸入</span><span class="sxs-lookup"><span data-stu-id="eed55-102">User Input in Windows Forms</span></span>
<span data-ttu-id="eed55-103">Windows Form 包含一種使用者輸入模型，這種模型是以在處理相關 Windows 訊息時所引發的事件為基礎。</span><span class="sxs-lookup"><span data-stu-id="eed55-103">Windows Forms includes a user input model based on events that are raised while processing related Windows messages.</span></span> <span data-ttu-id="eed55-104">本節中的主題提供滑鼠和鍵盤使用者輸入的相關資訊，包括示範如何執行特定工作的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="eed55-104">The topics in this section provide information on mouse and keyboard user input, including code examples that demonstrate how to perform specific tasks.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eed55-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="eed55-105">In This Section</span></span>  
 [<span data-ttu-id="eed55-106">Windows Forms 應用程式中的使用者輸入</span><span class="sxs-lookup"><span data-stu-id="eed55-106">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="eed55-107">提供使用者輸入事件的概觀和處理 Windows 訊息的方法。</span><span class="sxs-lookup"><span data-stu-id="eed55-107">Provides an overview of user input events and the methods that process Windows messages.</span></span>  
  
 [<span data-ttu-id="eed55-108">Windows Forms 應用程式中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="eed55-108">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="eed55-109">提供鍵盤訊息處理、不同按鍵類型和鍵盤事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eed55-109">Provides information on keyboard message handling, the different types of keys, and the keyboard events.</span></span>  
  
 [<span data-ttu-id="eed55-110">Windows Forms 應用程式中的滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="eed55-110">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 <span data-ttu-id="eed55-111">提供滑鼠事件和其他滑鼠相關功能 (包括滑鼠游標和滑鼠捕捉) 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eed55-111">Provides information on the mouse events and other mouse-related features, including mouse cursors and mouse capture.</span></span>  
  
 [<span data-ttu-id="eed55-112">操作說明：以程式碼模擬滑鼠和鍵盤事件</span><span class="sxs-lookup"><span data-stu-id="eed55-112">How to: Simulate Mouse and Keyboard Events in Code</span></span>](../../../docs/framework/winforms/how-to-simulate-mouse-and-keyboard-events-in-code.md)  
 <span data-ttu-id="eed55-113">示範以程式設計方式模擬滑鼠和鍵盤輸入的幾種不同方法。</span><span class="sxs-lookup"><span data-stu-id="eed55-113">Demonstrates several different ways to programmatically simulate mouse and keyboard input.</span></span>  
  
 [<span data-ttu-id="eed55-114">操作說明：處理 Windows Forms 控制項中的使用者輸入事件</span><span class="sxs-lookup"><span data-stu-id="eed55-114">How to: Handle User Input Events in Windows Forms Controls</span></span>](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md)  
 <span data-ttu-id="eed55-115">顯示處理大部分使用者輸入事件和報告每個事件相關資訊的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="eed55-115">Presents a code example that handles most user input events and reports information about each event.</span></span>  
  
 [<span data-ttu-id="eed55-116">Windows Forms 中的使用者輸入驗證</span><span class="sxs-lookup"><span data-stu-id="eed55-116">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 <span data-ttu-id="eed55-117">描述在 Windows Form 應用程式中驗證使用者輸入的方法。</span><span class="sxs-lookup"><span data-stu-id="eed55-117">Describes the methods to validate user input in Windows Forms applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eed55-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="eed55-118">Related Sections</span></span>  
 <span data-ttu-id="eed55-119">另請參閱[在 Windows Forms 中建立事件處理常式](https://msdn.microsoft.com/library/dacysss4\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="eed55-119">Also see [Creating Event Handlers in Windows Forms](https://msdn.microsoft.com/library/dacysss4\(v=vs.110\)).</span></span>
