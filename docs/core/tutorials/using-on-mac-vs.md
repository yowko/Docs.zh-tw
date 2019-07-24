---
title: 使用 Visual Studio for Mac 在 macOS 上開始使用 .NET Core
description: 本主題會逐步引導您使用 Visual Studio for Mac 和 .NET Core 建置簡單主控台應用程式。
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: a6d58d2a54ce9742542a3f7e5c9378be89b8f89a
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870527"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="99c01-103">使用 Visual Studio for Mac 在 macOS 上開始使用 .NET Core</span><span class="sxs-lookup"><span data-stu-id="99c01-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="99c01-104">Visual Studio for Mac 針對開發 .NET Core 應用程式，提供功能完整的整合式開發環境 (IDE)。</span><span class="sxs-lookup"><span data-stu-id="99c01-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="99c01-105">本主題會逐步引導您使用 Visual Studio for Mac 和 .NET Core 建置簡單主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="99c01-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="99c01-106">我們非常重視您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="99c01-106">Your feedback is highly valued.</span></span> <span data-ttu-id="99c01-107">您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：</span><span class="sxs-lookup"><span data-stu-id="99c01-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="99c01-108">在 Visual Studio for Mac 中，從功能表選取 [說明]   > [回報問題]  ，或從歡迎畫面選取 [回報問題]  ，這會開啟用來提出錯誤報告的視窗。</span><span class="sxs-lookup"><span data-stu-id="99c01-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="99c01-109">您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/8/index.html)入口網站追蹤您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="99c01-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="99c01-110">若要提出建議，請從功能表選取 [說明]   > [提供建議]  ，或從歡迎畫面選取 [提供建議]  ，這會帶您前往 [Visual Studio for Mac 開發人員社群網頁](https://developercommunity.visualstudio.com/content/idea/post.html?space=41) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="99c01-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99c01-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="99c01-111">Prerequisites</span></span>

<span data-ttu-id="99c01-112">請參閱 [Mac 上 .NET Core 的先決條件](../../core/macos-prerequisites.md)主題。</span><span class="sxs-lookup"><span data-stu-id="99c01-112">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

<span data-ttu-id="99c01-113">請查看 [.NET Core 支援](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019)指南以確定您使用的是支援的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="99c01-113">Check the [.NET Core Support](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) guide to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="99c01-114">開始使用</span><span class="sxs-lookup"><span data-stu-id="99c01-114">Get started</span></span>

<span data-ttu-id="99c01-115">如果您已經安裝必要條件和 Visual Studio for Mac，請略過本節並移至[建立專案](#creating-a-project)。</span><span class="sxs-lookup"><span data-stu-id="99c01-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="99c01-116">請遵循下列步驟來安裝必要條件和 Visual Studio for Mac：</span><span class="sxs-lookup"><span data-stu-id="99c01-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="99c01-117">下載 [Visual Studio for Mac 安裝程式](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。</span><span class="sxs-lookup"><span data-stu-id="99c01-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="99c01-118">執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="99c01-118">Run the installer.</span></span> <span data-ttu-id="99c01-119">閱讀並接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="99c01-119">Read and accept the license agreement.</span></span> <span data-ttu-id="99c01-120">在安裝期間，請選取安裝 .NET Core 的選項。</span><span class="sxs-lookup"><span data-stu-id="99c01-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="99c01-121">系統會詢問您是否要安裝 Xamarin，這是一個跨平台的行動應用程式開發技術。</span><span class="sxs-lookup"><span data-stu-id="99c01-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="99c01-122">針對 .NET Core 開發，安裝 Xamarin 和其相關元件為選擇性。</span><span class="sxs-lookup"><span data-stu-id="99c01-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="99c01-123">如需 Visual Studio for Mac 安裝程序的逐步解說，請參閱 [Visual Studio for Mac 文件](/visualstudio/mac/)。</span><span class="sxs-lookup"><span data-stu-id="99c01-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="99c01-124">安裝完成後，請啟動 Visual Studio for Mac IDE。</span><span class="sxs-lookup"><span data-stu-id="99c01-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="99c01-125">建立專案</span><span class="sxs-lookup"><span data-stu-id="99c01-125">Creating a project</span></span>

1. <span data-ttu-id="99c01-126">在 [開始] 視窗上，選取 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="99c01-126">Select **New** on the Start Window.</span></span>

   ![Visual Studio for Mac [開始] 畫面上的 [新增] 按鈕](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="99c01-128">在 [新增專案]  對話方塊中，選取 [.NET Core]  節點下的 [應用程式]  。</span><span class="sxs-lookup"><span data-stu-id="99c01-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="99c01-129">選取 [主控台應用程式]  範本，接著選取 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="99c01-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![[新增專案] 範本清單](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="99c01-131">如果您已安裝多個版本的 .NET Core，請針對您的專案選取目標 Framework。</span><span class="sxs-lookup"><span data-stu-id="99c01-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="99c01-132">針對 [專案名稱]  輸入 "HelloWorld"。</span><span class="sxs-lookup"><span data-stu-id="99c01-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="99c01-133">選取 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="99c01-133">Select **Create**.</span></span>

   ![設定新主控台應用程式對話方塊](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="99c01-135">等候專案的相依性還原完畢。</span><span class="sxs-lookup"><span data-stu-id="99c01-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="99c01-136">專案具有單一 C# 檔案 *Program.cs*，其中包含具有 `Main` 方法的 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="99c01-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="99c01-137">執行應用程式時，`Console.WriteLine` 陳述式會將 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="99c01-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="99c01-138">輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="99c01-138">to the console when the app is run.</span></span>

   ![開啟 Program.cs 檔案的主視窗](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="99c01-140">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="99c01-140">Run the application</span></span>

<span data-ttu-id="99c01-141">使用 ⌘ ↵ (command + enter) 以在偵錯模式中執行應用程式，或是使用 ⌥ ⌘ ↵ (option + command + enter) 以在發行模式中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="99c01-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![[應用程式輸出] 窗格顯示 Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="99c01-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="99c01-143">Next step</span></span>

<span data-ttu-id="99c01-144">[使用 Visual Studio for Mac 在 macOS 上建置完整的 .NET Core 解決方案](using-on-mac-vs-full-solution.md)主題，能說明如何建置一個包含可重複使用之程式庫和單元測試的完整 .NET Core 解決方案。</span><span class="sxs-lookup"><span data-stu-id="99c01-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
