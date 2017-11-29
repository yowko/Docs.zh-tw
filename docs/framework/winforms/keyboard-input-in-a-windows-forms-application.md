---
title: "Windows Forms 應用程式中的鍵盤輸入"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard input [Windows Forms], using in Windows Forms
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 68f5bc70-14d5-45c9-b288-7d7b1493ee79
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9d0c50fe8f99df471376d31a2258912c870dd37
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="keyboard-input-in-a-windows-forms-application"></a><span data-ttu-id="c5dc0-102">Windows Forms 應用程式中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="c5dc0-102">Keyboard Input in a Windows Forms Application</span></span>
<span data-ttu-id="c5dc0-103">Windows Form 包含可讓您回應特定按鍵，並提供方法讓您攔截、 修改和使用在應用程式中，表單中，按下按鍵及控制層級的標準鍵盤事件。</span><span class="sxs-lookup"><span data-stu-id="c5dc0-103">Windows Forms includes standard keyboard events that allow you to respond to specific key presses, and also provides ways for you to intercept, modify, and consume key presses at the application, form, and control level.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5dc0-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="c5dc0-104">In This Section</span></span>  
 [<span data-ttu-id="c5dc0-105">鍵盤輸入的運作方式</span><span class="sxs-lookup"><span data-stu-id="c5dc0-105">How Keyboard Input Works</span></span>](../../../docs/framework/winforms/how-keyboard-input-works.md)  
 <span data-ttu-id="c5dc0-106">描述如何鍵盤訊息處理和轉換成鍵盤事件。</span><span class="sxs-lookup"><span data-stu-id="c5dc0-106">Describes how keyboard messages are processed and transformed into keyboard events.</span></span>  
  
 [<span data-ttu-id="c5dc0-107">使用鍵盤事件</span><span class="sxs-lookup"><span data-stu-id="c5dc0-107">Using Keyboard Events</span></span>](../../../docs/framework/winforms/using-keyboard-events.md)  
 <span data-ttu-id="c5dc0-108">提供的鍵盤事件和鍵盤事件處理常式收到的資訊類型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c5dc0-108">Provides information on the types of keyboard events and the information that is received by the keyboard event handlers.</span></span>  
  
 [<span data-ttu-id="c5dc0-109">操作說明：將鍵盤輸入修改為標準控制項</span><span class="sxs-lookup"><span data-stu-id="c5dc0-109">How to: Modify Keyboard Input to a Standard Control</span></span>](../../../docs/framework/winforms/how-to-modify-keyboard-input-to-a-standard-control.md)  
 <span data-ttu-id="c5dc0-110">提供的程式碼範例示範如何修改它們到達控制項之前的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="c5dc0-110">Presents a code example that shows how to modify key values before they reach a control.</span></span>  
  
 [<span data-ttu-id="c5dc0-111">操作說明：判斷所按的輔助按鍵為何</span><span class="sxs-lookup"><span data-stu-id="c5dc0-111">How to: Determine Which Modifier Key Was Pressed</span></span>](../../../docs/framework/winforms/how-to-determine-which-modifier-key-was-pressed.md)  
 <span data-ttu-id="c5dc0-112">示範如何找出除了另一個索引鍵是否按下 SHIFT、 ALT 或 ctrl 鍵。</span><span class="sxs-lookup"><span data-stu-id="c5dc0-112">Demonstrates how to find out whether SHIFT, ALT, or CTRL was pressed in addition to another key.</span></span>  
  
 [<span data-ttu-id="c5dc0-113">操作說明：處理表單層級的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="c5dc0-113">How to: Handle Keyboard Input at the Form Level</span></span>](../../../docs/framework/winforms/how-to-handle-keyboard-input-at-the-form-level.md)  
 <span data-ttu-id="c5dc0-114">提供的程式碼範例示範如何攔截這些到達控制項之前的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c5dc0-114">Presents a code example that shows how to intercept keys before they reach a control.</span></span>
