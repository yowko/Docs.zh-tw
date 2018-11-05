---
title: 多檔案組件
ms.date: 03/30/2017
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
ms.openlocfilehash: f319ef94a5a0f1a5239a2f506386dbc15f0505ef
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846418"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="89021-102">多檔案組件</span><span class="sxs-lookup"><span data-stu-id="89021-102">Multifile Assemblies</span></span>

<span data-ttu-id="89021-103">您可以搭配使用命令列編譯器或 Visual Studio 與 Visual C++，來建立多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="89021-103">You can create multifile assemblies using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="89021-104">組件中的一個檔案必須包含組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="89021-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="89021-105">啟動應用程式的組件也必須包含進入點，例如 Main 或 WinMain 方法。</span><span class="sxs-lookup"><span data-stu-id="89021-105">An assembly that starts an application must also contain an entry point, such as a Main or WinMain method.</span></span>

<span data-ttu-id="89021-106">例如，假設您的應用程式包含兩個程式碼模組：Client.cs 和 Stringer.cs。</span><span class="sxs-lookup"><span data-stu-id="89021-106">For example, suppose you have an application that contains two code modules, Client.cs and Stringer.cs.</span></span> <span data-ttu-id="89021-107">Stringer.cs 會建立 Client.cs 中程式碼所參考的 `myStringer` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="89021-107">Stringer.cs creates the `myStringer` namespace that is referenced by the code in Client.cs.</span></span> <span data-ttu-id="89021-108">Client.cs 包含 `Main` 方法，而此方法是應用程式進入點。</span><span class="sxs-lookup"><span data-stu-id="89021-108">Client.cs contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="89021-109">在此範例中，您會編譯這兩個程式碼模組，然後建立包含組件資訊清單的第三個檔案，而組件資訊清單可啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="89021-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="89021-110">組件資訊清單同時參考 `Client` 和 `Stringer` 模組。</span><span class="sxs-lookup"><span data-stu-id="89021-110">The assembly manifest references both the `Client` and `Stringer` modules.</span></span>

> [!NOTE]
> <span data-ttu-id="89021-111">多檔案組件只能有一個進入點，即使組件有多個程式碼模組也是一樣。</span><span class="sxs-lookup"><span data-stu-id="89021-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="89021-112">您有數個原因可能想要建立多檔案組件：</span><span class="sxs-lookup"><span data-stu-id="89021-112">There are several reasons you might want to create a multifile assembly:</span></span>

-   <span data-ttu-id="89021-113">合併以不同語言撰寫的模組。</span><span class="sxs-lookup"><span data-stu-id="89021-113">To combine modules written in different languages.</span></span> <span data-ttu-id="89021-114">這是建立多檔案組件的最常見原因。</span><span class="sxs-lookup"><span data-stu-id="89021-114">This is the most common reason for creating a multifile assembly.</span></span>

-   <span data-ttu-id="89021-115">將很少使用的類型放在需要時才下載的模組中，以最佳化應用程式的下載。</span><span class="sxs-lookup"><span data-stu-id="89021-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="89021-116">如果您要使用 Microsoft Internet Explorer 建立將使用 `<object>` 標記所下載的應用程式，則一定要建立多檔案組件。</span><span class="sxs-lookup"><span data-stu-id="89021-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="89021-117">在此情況下，您會建立與程式碼模組不同的檔案，而此檔案只包含組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="89021-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="89021-118">Internet Explorer 會先下載組件資訊清單，然後建立背景工作執行緒來下載所需的任何額外模組或組件。</span><span class="sxs-lookup"><span data-stu-id="89021-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="89021-119">正在下載包含組件資訊清單的檔案時，Internet Explorer 不會回應使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="89021-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="89021-120">包含組件資訊清單的檔案越小，Internet Explorer 無回應的時間就越短。</span><span class="sxs-lookup"><span data-stu-id="89021-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

-   <span data-ttu-id="89021-121">合併數個開發人員所撰寫的程式碼模組。</span><span class="sxs-lookup"><span data-stu-id="89021-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="89021-122">雖然每個開發人員都可以將每個程式碼模組編譯為組件，但是將所有模組都放入多檔案組件時，這個動作會將某些未公開的類型強制為公開。</span><span class="sxs-lookup"><span data-stu-id="89021-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="89021-123">在您建立組件之後，可以簽署包含組件資訊清單 (因此包含組件) 的檔案，也可以指定檔案 (和組件) 的強式名稱，並將它放在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="89021-123">Once you create the assembly, you can sign the file that contains the assembly manifest (and hence the assembly), or you can give the file (and the assembly) a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="89021-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89021-124">See Also</span></span>

- [<span data-ttu-id="89021-125">操作說明：建置多檔案組件</span><span class="sxs-lookup"><span data-stu-id="89021-125">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="89021-126">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="89021-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)