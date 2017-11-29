---
title: "型別提供者安全性"
description: "深入了解在 F # 中，包括如何變更型別提供者的信任設定的型別提供者安全性。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9c5a8a1f-5a31-490d-83c0-8beabda75c78
ms.openlocfilehash: c8f03ee90d4dce1d3484a9dfe8951d500d509a2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="type-provider-security"></a><span data-ttu-id="5adef-104">型別提供者安全性</span><span class="sxs-lookup"><span data-stu-id="5adef-104">Type Provider Security</span></span>

<span data-ttu-id="5adef-105">型別提供者是包含組件 (Dll) 參考 F # 專案或指令碼的程式碼，以連接至外部資料來源和 F # 型別環境介面此類型資訊。</span><span class="sxs-lookup"><span data-stu-id="5adef-105">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="5adef-106">通常，當您編譯和接著執行程式碼 （或指令碼時，請將驗證碼傳送至 F # Interactive），是只執行參考組件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5adef-106">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="5adef-107">不過，型別提供者組件會執行在 Visual Studio 中，只是在編輯器中瀏覽程式碼時。</span><span class="sxs-lookup"><span data-stu-id="5adef-107">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="5adef-108">這是因為型別提供者需要執行額外的資訊加入至編輯器，例如快速諮詢工具提示，IntelliSense 完成等等。</span><span class="sxs-lookup"><span data-stu-id="5adef-108">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="5adef-109">如此一來，有額外的安全性考量的型別提供者組件，因為它們會自動執行 Visual Studio 處理序內。</span><span class="sxs-lookup"><span data-stu-id="5adef-109">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>


## <a name="security-warning-dialog"></a><span data-ttu-id="5adef-110">安全性警告對話方塊</span><span class="sxs-lookup"><span data-stu-id="5adef-110">Security Warning Dialog</span></span>
<span data-ttu-id="5adef-111">當第一次使用特定型別提供者組件，Visual Studio 會顯示 [安全性] 對話方塊會警告您的型別提供者即將執行。</span><span class="sxs-lookup"><span data-stu-id="5adef-111">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="5adef-112">Visual Studio 會載入型別提供者之前，它讓您決定是否信任這個特定的提供者。</span><span class="sxs-lookup"><span data-stu-id="5adef-112">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="5adef-113">如果您信任來源的型別提供者，然後選取 我信任此型別提供者 」。</span><span class="sxs-lookup"><span data-stu-id="5adef-113">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="5adef-114">如果您不信任來源的型別提供者，然後選取 我不信任此型別提供者。 」</span><span class="sxs-lookup"><span data-stu-id="5adef-114">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="5adef-115">信任的提供者，讓它能夠在 Visual Studio 內執行，並提供 IntelliSense 然後建置功能。</span><span class="sxs-lookup"><span data-stu-id="5adef-115">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="5adef-116">但是，如果惡意型別提供者本身，執行其程式碼可能會危及您的電腦。</span><span class="sxs-lookup"><span data-stu-id="5adef-116">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="5adef-117">如果您的專案包含參考型別提供者，您選擇在對話方塊中不信任的程式碼，然後在編譯時期，編譯器會回報錯誤，指出類型提供者未受信任。</span><span class="sxs-lookup"><span data-stu-id="5adef-117">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="5adef-118">任何相依於不受信任的類型提供者的類型會以紅色波浪線表示。</span><span class="sxs-lookup"><span data-stu-id="5adef-118">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="5adef-119">它可以安全地瀏覽程式碼編輯器中。</span><span class="sxs-lookup"><span data-stu-id="5adef-119">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="5adef-120">如果您決定要變更的信任設定，直接在 Visual Studio 中，執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="5adef-120">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>


#### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="5adef-121">若要變更型別提供者信任設定</span><span class="sxs-lookup"><span data-stu-id="5adef-121">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="5adef-122">在`Tools`功能表上，選取`Options`，然後展開`F# Tools`節點。</span><span class="sxs-lookup"><span data-stu-id="5adef-122">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>
<br />

2. <span data-ttu-id="5adef-123">選取`Type Providers`中的型別提供者清單中，選取核取方塊的型別提供者信任時，和不信任的清除核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5adef-123">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="5adef-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5adef-124">See Also</span></span>
[<span data-ttu-id="5adef-125">類型提供者</span><span class="sxs-lookup"><span data-stu-id="5adef-125">Type Providers</span></span>](index.md)
