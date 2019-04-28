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
ms.openlocfilehash: 0baf54d27cf33eef7e4df7019ee98b42eba40205
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011797"
---
# <a name="backgroundworker-component"></a><span data-ttu-id="c5447-102">BackgroundWorker 元件</span><span class="sxs-lookup"><span data-stu-id="c5447-102">BackgroundWorker Component</span></span>
<span data-ttu-id="c5447-103">`BackgroundWorker`元件可讓您的表單或控制項非同步執行作業。</span><span class="sxs-lookup"><span data-stu-id="c5447-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5447-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="c5447-104">In This Section</span></span>  
 [<span data-ttu-id="c5447-105">BackgroundWorker 元件概觀</span><span class="sxs-lookup"><span data-stu-id="c5447-105">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="c5447-106">描述`BackgroundWorker`元件，可讓您能夠執行這些耗時的作業，以非同步方式 （「 在背景中 」），不同於您的應用程式主要 UI 執行緒的執行緒上。</span><span class="sxs-lookup"><span data-stu-id="c5447-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="c5447-107">逐步解說：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="c5447-107">Walkthrough: Running an Operation in the Background</span></span>](walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="c5447-108">示範如何使用`BackgroundWorker`元件在設計工具中執行耗時的作業，在個別執行緒上。</span><span class="sxs-lookup"><span data-stu-id="c5447-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="c5447-109">如何：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="c5447-109">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="c5447-110">示範如何使用`BackgroundWorker`元件來執行耗時的作業，在個別執行緒上。</span><span class="sxs-lookup"><span data-stu-id="c5447-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="c5447-111">逐步解說：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="c5447-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="c5447-112">建立以非同步方式進行算術運算的設計工具的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5447-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="c5447-113">如何：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="c5447-113">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="c5447-114">建立以非同步方式進行算術運算的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5447-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="c5447-115">如何：在背景將檔案下載</span><span class="sxs-lookup"><span data-stu-id="c5447-115">How to: Download a File in the Background</span></span>](how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="c5447-116">示範如何使用`BackgroundWorker`元件，以下載個別的執行緒上的檔案。</span><span class="sxs-lookup"><span data-stu-id="c5447-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c5447-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="c5447-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="c5447-118">說明這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="c5447-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="c5447-119">描述保留的資料型別<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件。</span><span class="sxs-lookup"><span data-stu-id="c5447-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="c5447-120">描述保留的資料型別<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="c5447-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c5447-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="c5447-121">Related Sections</span></span>  
 [<span data-ttu-id="c5447-122">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="c5447-122">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="c5447-123">描述如何以非同步模式提供多執行緒的應用程式的優點同時隱藏許多多執行緒設計中原有的複雜問題。</span><span class="sxs-lookup"><span data-stu-id="c5447-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>
