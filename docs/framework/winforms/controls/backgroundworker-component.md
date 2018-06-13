---
title: BackgroundWorker 元件
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
ms.openlocfilehash: 38505876e2f944139622a0d7cf7aaab9c510ef89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525748"
---
# <a name="backgroundworker-component"></a><span data-ttu-id="5c686-102">BackgroundWorker 元件</span><span class="sxs-lookup"><span data-stu-id="5c686-102">BackgroundWorker Component</span></span>
<span data-ttu-id="5c686-103">`BackgroundWorker`元件可讓您的表單或控制項加入執行非同步作業。</span><span class="sxs-lookup"><span data-stu-id="5c686-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c686-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="5c686-104">In This Section</span></span>  
 [<span data-ttu-id="5c686-105">BackgroundWorker 元件概觀</span><span class="sxs-lookup"><span data-stu-id="5c686-105">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="5c686-106">描述`BackgroundWorker`元件，可讓您執行這些耗時的作業，以非同步方式 （「 在背景中 」），不同於您的應用程式的主要 UI 執行緒的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5c686-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="5c686-107">逐步解說：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="5c686-107">Walkthrough: Running an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="5c686-108">示範如何使用`BackgroundWorker`元件在設計工具中執行耗時的作業，另一個執行緒上。</span><span class="sxs-lookup"><span data-stu-id="5c686-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="5c686-109">操作說明：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="5c686-109">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="5c686-110">示範如何使用`BackgroundWorker`元件來執行耗時的作業，另一個執行緒上。</span><span class="sxs-lookup"><span data-stu-id="5c686-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="5c686-111">逐步解說：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="5c686-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="5c686-112">建立使用設計工具會以非同步方式執行算術運算的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c686-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="5c686-113">操作說明：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="5c686-113">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="5c686-114">建立的應用程式，以非同步方式進行算術運算。</span><span class="sxs-lookup"><span data-stu-id="5c686-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="5c686-115">操作說明：在背景中下載檔案</span><span class="sxs-lookup"><span data-stu-id="5c686-115">How to: Download a File in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="5c686-116">示範如何使用`BackgroundWorker`元件下載個別的執行緒上的檔案。</span><span class="sxs-lookup"><span data-stu-id="5c686-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5c686-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="5c686-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="5c686-118">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="5c686-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="5c686-119">描述保留的資料類型<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件。</span><span class="sxs-lookup"><span data-stu-id="5c686-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="5c686-120">描述保留的資料類型<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="5c686-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5c686-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="5c686-121">Related Sections</span></span>  
 [<span data-ttu-id="5c686-122">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="5c686-122">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="5c686-123">描述如何以非同步模式提供多執行緒應用程式的優點同時隱藏許多多執行緒設計中原有的複雜問題。</span><span class="sxs-lookup"><span data-stu-id="5c686-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>
