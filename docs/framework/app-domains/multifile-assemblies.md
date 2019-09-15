---
title: 多檔案元件
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4c288a54194e89eb90b6ac512cf45184376e952
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971869"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="56f13-102">多檔案元件</span><span class="sxs-lookup"><span data-stu-id="56f13-102">Multifile assemblies</span></span>

<span data-ttu-id="56f13-103">您可以使用命令列編譯器或 Visual Studio with Visual C++，建立以 .NET Framework 為目標的多檔案元件。</span><span class="sxs-lookup"><span data-stu-id="56f13-103">You can create multifile assemblies that target the .NET Framework using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="56f13-104">組件中的一個檔案必須包含組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="56f13-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="56f13-105">啟動應用程式的元件也必須包含進入點，例如`Main`或`WinMain`方法。</span><span class="sxs-lookup"><span data-stu-id="56f13-105">An assembly that starts an application must also contain an entry point, such as a `Main` or `WinMain` method.</span></span>

<span data-ttu-id="56f13-106">例如，假設您有一個應用程式，其中包含兩個程式碼模組： *Client.cs*和*Stringer.cs*。</span><span class="sxs-lookup"><span data-stu-id="56f13-106">For example, suppose you have an application that contains two code modules, *Client.cs* and *Stringer.cs*.</span></span> <span data-ttu-id="56f13-107">*Stringer.cs*會建立`myStringer` *Client.cs*中的程式碼所參考的命名空間。</span><span class="sxs-lookup"><span data-stu-id="56f13-107">*Stringer.cs* creates the `myStringer` namespace that is referenced by the code in *Client.cs*.</span></span> <span data-ttu-id="56f13-108">*Client.cs*包含`Main`方法，這是應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="56f13-108">*Client.cs* contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="56f13-109">在此範例中，您會編譯這兩個程式碼模組，然後建立包含組件資訊清單的第三個檔案，而組件資訊清單可啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="56f13-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="56f13-110">組件資訊清單會同時參考*用戶端*和*Stringer*模組。</span><span class="sxs-lookup"><span data-stu-id="56f13-110">The assembly manifest references both the *Client* and *Stringer* modules.</span></span>

> [!NOTE]
> <span data-ttu-id="56f13-111">多檔案組件只能有一個進入點，即使組件有多個程式碼模組也是一樣。</span><span class="sxs-lookup"><span data-stu-id="56f13-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="56f13-112">您有數個原因可能想要建立多檔案組件：</span><span class="sxs-lookup"><span data-stu-id="56f13-112">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="56f13-113">合併以不同語言撰寫的模組。</span><span class="sxs-lookup"><span data-stu-id="56f13-113">To combine modules written in different languages.</span></span> <span data-ttu-id="56f13-114">這是建立多檔案組件的最常見原因。</span><span class="sxs-lookup"><span data-stu-id="56f13-114">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="56f13-115">將很少使用的類型放在需要時才下載的模組中，以最佳化應用程式的下載。</span><span class="sxs-lookup"><span data-stu-id="56f13-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="56f13-116">如果您要使用 Microsoft Internet Explorer 建立將使用 `<object>` 標記所下載的應用程式，則一定要建立多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="56f13-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="56f13-117">在此情況下，您會建立與程式碼模組不同的檔案，而此檔案只包含組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="56f13-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="56f13-118">Internet Explorer 會先下載組件資訊清單，然後建立背景工作執行緒來下載所需的任何額外模組或組件。</span><span class="sxs-lookup"><span data-stu-id="56f13-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="56f13-119">正在下載包含組件資訊清單的檔案時，Internet Explorer 不會回應使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="56f13-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="56f13-120">包含組件資訊清單的檔案越小，Internet Explorer 無回應的時間就越短。</span><span class="sxs-lookup"><span data-stu-id="56f13-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="56f13-121">合併數個開發人員所撰寫的程式碼模組。</span><span class="sxs-lookup"><span data-stu-id="56f13-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="56f13-122">雖然每個開發人員都可以將每個程式碼模組編譯為組件，但是將所有模組都放入多檔案組件時，這個動作會將某些未公開的類型強制為公開。</span><span class="sxs-lookup"><span data-stu-id="56f13-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="56f13-123">建立元件之後，您可以簽署包含組件資訊清單的檔案，也就是元件，也可以為檔案和元件指定強式名稱，並將它放在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="56f13-123">Once you create the assembly, you can sign the file that contains the assembly manifest, and hence the assembly, or you can give the file and the assembly a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="56f13-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56f13-124">See also</span></span>

- [<span data-ttu-id="56f13-125">如何：建立多檔案元件</span><span class="sxs-lookup"><span data-stu-id="56f13-125">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="56f13-126">具有元件的程式</span><span class="sxs-lookup"><span data-stu-id="56f13-126">Program with assemblies</span></span>](../../standard/assembly/program.md)
