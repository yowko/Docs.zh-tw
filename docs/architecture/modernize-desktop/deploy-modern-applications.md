---
title: 部署現代化傳統型應用程式
description: 部署新式桌面應用程式所需瞭解的一切。
ms.date: 05/12/2020
ms.openlocfilehash: 4a4d93caf1c2f8f58d48ee3199bbe6983fa939f4
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423254"
---
# <a name="deploying-modern-desktop-applications"></a><span data-ttu-id="319f1-103">部署現代化傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="319f1-103">Deploying Modern Desktop Applications</span></span>

<span data-ttu-id="319f1-104">當您開發桌面應用程式時，要考慮的一件事是如何將應用程式封裝並部署到使用者的電腦。</span><span class="sxs-lookup"><span data-stu-id="319f1-104">When you develop desktop applications, one thing to consider is how your application is going to be packaged and deployed to the users' machines.</span></span> <span data-ttu-id="319f1-105">封裝、部署和安裝的問題是，它通常是在 IT 專業人員的範圍內，負責與開發人員不同的事物。</span><span class="sxs-lookup"><span data-stu-id="319f1-105">The problem with packaging, deployment, and installation is that it usually falls under the umbrella of the IT professionals, who care about different things than developers.</span></span>

<span data-ttu-id="319f1-106">這幾天，我們全都熟悉 DevOps 概念，讓開發人員和 IT 專業人員能夠密切地工作，將應用程式移至生產環境。</span><span class="sxs-lookup"><span data-stu-id="319f1-106">These days, we're all familiar with the DevOps concept, where developers and IT Pros work closely to move applications to their production environments.</span></span> <span data-ttu-id="319f1-107">但如果您在桌上型電腦上已有超過10年的時間，您可能會看到下列案例。</span><span class="sxs-lookup"><span data-stu-id="319f1-107">But if you've been in the desktop battle for more than 10 years, you might have seen the following story.</span></span> <span data-ttu-id="319f1-108">開發人員小組會一起工作，以符合專案的截止時間。</span><span class="sxs-lookup"><span data-stu-id="319f1-108">A team of developers works together hard to meet the project deadlines.</span></span> <span data-ttu-id="319f1-109">商務人員擔心，因為他們需要在許多使用者的電腦上工作，才能執行公司。</span><span class="sxs-lookup"><span data-stu-id="319f1-109">Business people are nervous since they need the system working on many user's machines to run the company.</span></span> <span data-ttu-id="319f1-110">在「D 天」，專案經理會向每位開發人員檢查其程式碼是否正常運作，而且一切都沒問題，因此可以出貨。</span><span class="sxs-lookup"><span data-stu-id="319f1-110">On "D-Day", the project manager checks with every developer that their code is working well and that everything is fine, so they can ship.</span></span> <span data-ttu-id="319f1-111">然後，套件小組會產生應用程式的設定、將其散發給每個使用者電腦，以及一組執行應用程式的測試使用者。</span><span class="sxs-lookup"><span data-stu-id="319f1-111">Then, the package team comes in generating the setup for the app, distribute it to every user machine and a set of test users run the application.</span></span> <span data-ttu-id="319f1-112">他們會嘗試，因為在顯示任何 UI 之前，應用程式會擲回例外狀況，指出「方法 ~ 物件 ~ 失敗」。</span><span class="sxs-lookup"><span data-stu-id="319f1-112">Well, they try, because before showing any UI, the application throws an exception that says "Method ~ of object ~ failed".</span></span> <span data-ttu-id="319f1-113">驚慌會開始流經空中，而簡短的調查則是指引進了協力廠商控制項的年輕開發人員，這當然是「在開發電腦上工作」。</span><span class="sxs-lookup"><span data-stu-id="319f1-113">Panic starts flowing through the air and a brief investigation points to a young and tired developer that has introduced a third-party control, that certainly "worked on the dev machine".</span></span>

<span data-ttu-id="319f1-114">傳統上，安裝桌面應用程式有兩個主要原因：</span><span class="sxs-lookup"><span data-stu-id="319f1-114">Installing desktop applications have traditionally been a nightmare for two main reasons:</span></span>

- <span data-ttu-id="319f1-115">開發人員與 IT 小組之間缺乏密切的共同作業文化特性。</span><span class="sxs-lookup"><span data-stu-id="319f1-115">Lack of close collaboration culture between dev and IT teams.</span></span>
- <span data-ttu-id="319f1-116">缺乏穩固的封裝和部署技術，我們可以建立。</span><span class="sxs-lookup"><span data-stu-id="319f1-116">Lack of a solid packaging and deploying technology we can build upon.</span></span>

<span data-ttu-id="319f1-117">事實上，我們一直在致歉您已安裝應用程式的情況，因為：</span><span class="sxs-lookup"><span data-stu-id="319f1-117">In fact, we've been living with the fact that sometimes you regret that you installed an app because:</span></span>

- <span data-ttu-id="319f1-118">最後，它會在您的電腦上產生一些不想要的副作用。</span><span class="sxs-lookup"><span data-stu-id="319f1-118">It ends up having some undesired side effects on your machine.</span></span>
- <span data-ttu-id="319f1-119">某些先前安裝的應用程式停止運作。</span><span class="sxs-lookup"><span data-stu-id="319f1-119">Some applications that were previously installed stop working.</span></span>

<span data-ttu-id="319f1-120">此外，您也無法藉由卸載應用程式，將系統還原到其原始狀態。</span><span class="sxs-lookup"><span data-stu-id="319f1-120">Additionally, you can't just restore the system to its original state by uninstalling the app.</span></span> <span data-ttu-id="319f1-121">我們一直在此情況下，我們已 alistair 創造「DLL Hell」或「Winrot」之類的詞彙。</span><span class="sxs-lookup"><span data-stu-id="319f1-121">We're so used to live this situation that we've coined terms like "DLL Hell" or "Winrot".</span></span>

<span data-ttu-id="319f1-122">在本章中，我們將討論 MSIX。</span><span class="sxs-lookup"><span data-stu-id="319f1-122">In this chapter, we'll talk about MSIX.</span></span> <span data-ttu-id="319f1-123">MSIX 是 Microsoft 的全新技術，會嘗試抓住先前的技術，為未來的封裝技術提供堅實的基礎。</span><span class="sxs-lookup"><span data-stu-id="319f1-123">MSIX is the brand-new technology from Microsoft that tries to capture the best of previous technologies to provide a solid foundation for the packaging technology of the future.</span></span>

<span data-ttu-id="319f1-124">封裝技術對現代化有何作用？</span><span class="sxs-lookup"><span data-stu-id="319f1-124">What does a packaging technology have to do with modernization?</span></span> <span data-ttu-id="319f1-125">事實上，封裝是企業 IT 的基礎，投資了許多錢。</span><span class="sxs-lookup"><span data-stu-id="319f1-125">Well, it turns out that packaging is fundamental for the enterprise IT with lots of money invested there.</span></span> <span data-ttu-id="319f1-126">現代化不僅與使用最新技術有關。</span><span class="sxs-lookup"><span data-stu-id="319f1-126">Modernization isn't only related to using the latest technologies.</span></span> <span data-ttu-id="319f1-127">它也與您在公司將功能傳遞給用戶端之前，從定義商務需求到市場的時間之間縮短上市的時機。</span><span class="sxs-lookup"><span data-stu-id="319f1-127">It's also related to reducing time to market from the moment a business requirement is defined until your company delivers the feature to your client.</span></span>

## <a name="the-modern-application-lifecycle"></a><span data-ttu-id="319f1-128">現代化應用程式生命週期</span><span class="sxs-lookup"><span data-stu-id="319f1-128">The modern application lifecycle</span></span>

<span data-ttu-id="319f1-129">現在，開發人員會撰寫並建立應用程式的程式碼，然後將產生的資產傳遞給 IT 專業人員。</span><span class="sxs-lookup"><span data-stu-id="319f1-129">Today, developers write and build the code for an app and then pass the generated assets to the IT Pros.</span></span> <span data-ttu-id="319f1-130">然後，IT 專業人員會重新設定應用程式，並將它重新封裝，通常是在 MSI 中，或最近採用 App-v 封裝格式。</span><span class="sxs-lookup"><span data-stu-id="319f1-130">Then, the IT Pros reconfigure the app and repackage it, typically in an MSI or more recently in an App-V packaging format.</span></span> <span data-ttu-id="319f1-131">然後，應用程式會透過不同的通道和工具進行部署。</span><span class="sxs-lookup"><span data-stu-id="319f1-131">The app is then deployed through different channels and tools.</span></span> <span data-ttu-id="319f1-132">這種方法的其中一個主要問題，通常稱為「封裝 paralysis」。</span><span class="sxs-lookup"><span data-stu-id="319f1-132">One of the main problems with this approach is commonly known as "packaging paralysis".</span></span> <span data-ttu-id="319f1-133">問題在於，每次有應用程式更新或作業系統更新時，此週期都會重複。</span><span class="sxs-lookup"><span data-stu-id="319f1-133">The problem is that this cycle repeats every time there's an app update or an OS update.</span></span>

<span data-ttu-id="319f1-134">您可以看到下列圖片所反映的程式：</span><span class="sxs-lookup"><span data-stu-id="319f1-134">You can see the process reflected on the following picture:</span></span>

![顯示現代化 IT 生命週期的圖表](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

<span data-ttu-id="319f1-136">公司需要將此封裝週期分成三個獨立週期的方法：</span><span class="sxs-lookup"><span data-stu-id="319f1-136">Companies need a way to break this packaging cycle into three independent cycles:</span></span>

- <span data-ttu-id="319f1-137">OS 更新</span><span class="sxs-lookup"><span data-stu-id="319f1-137">OS updates</span></span>
- <span data-ttu-id="319f1-138">應用程式更新</span><span class="sxs-lookup"><span data-stu-id="319f1-138">Application updates</span></span>
- <span data-ttu-id="319f1-139">自訂</span><span class="sxs-lookup"><span data-stu-id="319f1-139">Customization</span></span>

![顯示現代化 IT 良性週期的圖表](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

<span data-ttu-id="319f1-141">上圖顯示您可以：</span><span class="sxs-lookup"><span data-stu-id="319f1-141">The previous diagram shows that you can:</span></span>

- <span data-ttu-id="319f1-142">更新基礎作業系統，而不需要重新封裝您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-142">Update the underlying OS without having to repackage your apps.</span></span>
- <span data-ttu-id="319f1-143">不需要重新封裝原始開發人員套件，即可從該專案進行自訂。</span><span class="sxs-lookup"><span data-stu-id="319f1-143">Enable customizations from IT without the need to repackage the original developer package.</span></span>

<span data-ttu-id="319f1-144">這項基本變更會將我們帶到新的和現代化的 IT 生命週期，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="319f1-144">This radical change leads us to the new and modern IT lifecycle as shown in the following picture:</span></span>

![使用 Microsoft 工具顯示應用程式生命週期的圖表](./media/deploy-modern-applications/microsoft-it-tools.png)

<span data-ttu-id="319f1-146">開發人員建立應用程式並產生 MSIX 套件，IT 專業人員可以取用和設定，而不需要重新封裝。</span><span class="sxs-lookup"><span data-stu-id="319f1-146">Developers create the app and generate an MSIX package that IT Pros can consume and configure without the need of repackaging.</span></span> <span data-ttu-id="319f1-147">除了 MSIX 技術之外，Microsoft 還建立了一些工具，讓它可以自訂和設定套件，而不需要重新封裝。</span><span class="sxs-lookup"><span data-stu-id="319f1-147">Along with the MSIX technology, Microsoft has created tools to allow IT to customize and configure packages without repackaging.</span></span>

## <a name="msix-the-next-generation-of-deployment"></a><span data-ttu-id="319f1-148">MSIX：新一代部署</span><span class="sxs-lookup"><span data-stu-id="319f1-148">MSIX: The next generation of deployment</span></span>

<span data-ttu-id="319f1-149">在 MSIX 之前，有幾種封裝技術可供使用，像是安裝程式、MSI、ClickOnce、App-v 和腳本。</span><span class="sxs-lookup"><span data-stu-id="319f1-149">Before MSIX, there were several packaging technologies available like setup wizards, MSI, ClickOnce, App-V, and scripting.</span></span> <span data-ttu-id="319f1-150">這兩種技術都有自己的優勢，而 Microsoft 決定挑選最棒的組建 MSIX。</span><span class="sxs-lookup"><span data-stu-id="319f1-150">Each of these technologies has their own strengths and Microsoft has decided to pick the best of all to build MSIX.</span></span> <span data-ttu-id="319f1-151">MSIX 是建置於這些現有技術的基礎上，挑選出最佳的功能：</span><span class="sxs-lookup"><span data-stu-id="319f1-151">MSIX is built on the foundations of these existing technologies picking the best of each:</span></span>

- <span data-ttu-id="319f1-152">App-v = \> 容器化</span><span class="sxs-lookup"><span data-stu-id="319f1-152">App-V =\> Containerization</span></span>
- <span data-ttu-id="319f1-153">ClickOnce = \> 自動更新</span><span class="sxs-lookup"><span data-stu-id="319f1-153">ClickOnce =\> Auto updating</span></span>
- <span data-ttu-id="319f1-154">MSI = \> 容易散發</span><span class="sxs-lookup"><span data-stu-id="319f1-154">MSI =\> Easy to distribute</span></span>

<span data-ttu-id="319f1-155">透過 MSIX，您可以取得一項安裝程式技術，其中包含所有這些功能。</span><span class="sxs-lookup"><span data-stu-id="319f1-155">With MSIX, you get one installer technology with all these features.</span></span>

![此圖顯示對建立 MSIX 有影響的不同技術](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a><span data-ttu-id="319f1-157">MSIX 的優點</span><span class="sxs-lookup"><span data-stu-id="319f1-157">Benefits of MSIX</span></span>

#### <a name="never-regret-installing-an-app"></a><span data-ttu-id="319f1-158">永不致歉安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="319f1-158">Never regret installing an app</span></span>

<span data-ttu-id="319f1-159">MSIX 提供可預測、可靠且安全的部署。</span><span class="sxs-lookup"><span data-stu-id="319f1-159">MSIX provides a predictable, reliable, and safe deployment.</span></span> <span data-ttu-id="319f1-160">封裝資訊清單中包含的宣告式方法可讓 OS 追蹤您應用程式所需的每個資產。</span><span class="sxs-lookup"><span data-stu-id="319f1-160">The declarative method contained in the package manifest lets the OS keep track of every asset your application needs.</span></span> <span data-ttu-id="319f1-161">它也提供真正的全新卸載，而且沒有副作用。</span><span class="sxs-lookup"><span data-stu-id="319f1-161">It also provides a true clean uninstall with no side effects.</span></span>

#### <a name="disk-space-optimization"></a><span data-ttu-id="319f1-162">磁碟空間優化</span><span class="sxs-lookup"><span data-stu-id="319f1-162">Disk space optimization</span></span>

<span data-ttu-id="319f1-163">MSIX 已優化，可減少應用程式在使用者電腦磁碟空間上的使用量。</span><span class="sxs-lookup"><span data-stu-id="319f1-163">MSIX is optimized to reduce the footprint that an application has on the user's machine disk space.</span></span> <span data-ttu-id="319f1-164">它會建立檔案的儲存單一版本。</span><span class="sxs-lookup"><span data-stu-id="319f1-164">It creates a single instance storage of your files.</span></span> <span data-ttu-id="319f1-165">也就是說，如果您有兩個不同的套件具有相同的 DLL，則不會安裝 DLL 兩次。</span><span class="sxs-lookup"><span data-stu-id="319f1-165">That is, if you have two different packages with the same DLL, the DLL isn't installed twice.</span></span> <span data-ttu-id="319f1-166">平臺會處理這個問題，因為它知道特定應用程式已安裝的所有檔案，因為它的宣告式本質。</span><span class="sxs-lookup"><span data-stu-id="319f1-166">The platform takes care of that problem because it knows all the files that a particular app installed thanks to its declarative nature.</span></span> <span data-ttu-id="319f1-167">它也可讓您讓不同版本的 DLL 並存運作。</span><span class="sxs-lookup"><span data-stu-id="319f1-167">It also allows you to have different versions of a DLL working side by side.</span></span>

<span data-ttu-id="319f1-168">使用資源套件時，您可以輕鬆地建立多語系應用程式，而 OS 會負責安裝所使用的。</span><span class="sxs-lookup"><span data-stu-id="319f1-168">With the use of resource packages, you can easily create multilingual apps and the OS takes care of installing the ones that are used.</span></span>

#### <a name="network-optimization"></a><span data-ttu-id="319f1-169">網路優化</span><span class="sxs-lookup"><span data-stu-id="319f1-169">Network optimization</span></span>

<span data-ttu-id="319f1-170">MSIX 會偵測位元組區塊層級的檔案差異，並啟用稱為「差異更新」的功能。</span><span class="sxs-lookup"><span data-stu-id="319f1-170">MSIX detects the differences on the files at the byte block level enabling a feature called differential updates.</span></span> <span data-ttu-id="319f1-171">這表示，只有更新的位元組區塊會在應用程式更新時下載。</span><span class="sxs-lookup"><span data-stu-id="319f1-171">What this means is that only the updated byte blocks are downloaded on application updates.</span></span>

![顯示 MSIX 如何管理差異更新的圖表](./media/deploy-modern-applications/msix-managing-updates.png)

<span data-ttu-id="319f1-173">使用串流安裝時，使用者可以快速開始使用您的應用程式，而應用程式的其他部分則會在背景下載。</span><span class="sxs-lookup"><span data-stu-id="319f1-173">With streaming installation, the user can quickly start working on your application while other parts of the app are downloaded on the background.</span></span> <span data-ttu-id="319f1-174">這項功能可為您的使用者提供吸引人的體驗。</span><span class="sxs-lookup"><span data-stu-id="319f1-174">This feature contributes to an engaging experience for your users.</span></span>

<span data-ttu-id="319f1-175">使用選擇性套件功能時，您可以在應用程式部署上達成元件化，以便在需要時下載。</span><span class="sxs-lookup"><span data-stu-id="319f1-175">With the optional packages feature, you achieve componentization on your app deployment, so you can download them when needed.</span></span>

#### <a name="simple-packaging-and-deployment"></a><span data-ttu-id="319f1-176">簡單封裝和部署</span><span class="sxs-lookup"><span data-stu-id="319f1-176">Simple packaging and deployment</span></span>

<span data-ttu-id="319f1-177">此 AppManifest 會宣告每個應用程式的版本控制、裝置目標和識別（以標準方式表示）。</span><span class="sxs-lookup"><span data-stu-id="319f1-177">The AppManifest declares the versioning, device targeting and identify in a standard way for every application.</span></span> <span data-ttu-id="319f1-178">它也提供一種方式來簽署您的資產，以提供穩固的安全性基礎。</span><span class="sxs-lookup"><span data-stu-id="319f1-178">It also provides a way to sign your assets providing a solid security foundation.</span></span>

#### <a name="os-managed"></a><span data-ttu-id="319f1-179">作業系統管理</span><span class="sxs-lookup"><span data-stu-id="319f1-179">OS managed</span></span>

<span data-ttu-id="319f1-180">OS 會處理所有用來安裝、更新和移除應用程式的進程。</span><span class="sxs-lookup"><span data-stu-id="319f1-180">The OS handles all the processes for installing, updating, and removing an application.</span></span> <span data-ttu-id="319f1-181">應用程式會針對每個使用者安裝，但只下載一次，可將磁片使用量降到最低。</span><span class="sxs-lookup"><span data-stu-id="319f1-181">Applications are installed per user but downloaded only once, minimizing the disk footprint.</span></span> <span data-ttu-id="319f1-182">Microsoft 正致力於在 Windows 7 上提供 MSIX 體驗。</span><span class="sxs-lookup"><span data-stu-id="319f1-182">Microsoft is working on providing the MSIX experience also on Windows 7.</span></span>

#### <a name="windows-provides-integrity-for-the-app"></a><span data-ttu-id="319f1-183">Windows 提供應用程式的完整性</span><span class="sxs-lookup"><span data-stu-id="319f1-183">Windows provides integrity for the app</span></span>

<span data-ttu-id="319f1-184">使用數位簽章時，您可以保證不會從不受信任的來源安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-184">With the use of digital signatures, you can guarantee that you don't install an application from untrusted sources.</span></span> <span data-ttu-id="319f1-185">MSIX 也會防止進行篡改，原因如下：</span><span class="sxs-lookup"><span data-stu-id="319f1-185">MSIX also prevents tampering because:</span></span>

- <span data-ttu-id="319f1-186">它會保留檔案雜湊的記錄。</span><span class="sxs-lookup"><span data-stu-id="319f1-186">It keeps a record of file hashes.</span></span>
- <span data-ttu-id="319f1-187">它會偵測檔案在安裝後是否已修改。</span><span class="sxs-lookup"><span data-stu-id="319f1-187">It detects if a file has been modified after installation.</span></span>

#### <a name="works-for-the-entire-app-catalog"></a><span data-ttu-id="319f1-188">適用于整個應用程式類別目錄</span><span class="sxs-lookup"><span data-stu-id="319f1-188">Works for the entire App Catalog</span></span>

<span data-ttu-id="319f1-189">MSIX 的其中一個最酷事項是，它適用于整個應用程式類別目錄、Windows Forms、WPF、MFC/ATL、Delphi，即使您想要執行 xCopy 部署、ClickOnce 或前往存放區，您還是可以使用相同的 MSIX 封裝。</span><span class="sxs-lookup"><span data-stu-id="319f1-189">One of the coolest things about MSIX is that it works for the entire application catalog, Windows Forms, WPF, MFC/ATL, Delphi, even if you want to do xCopy deployment, ClickOnce, or going to the Store, you can use the same MSIX package.</span></span>

### <a name="tools"></a><span data-ttu-id="319f1-190">工具</span><span class="sxs-lookup"><span data-stu-id="319f1-190">Tools</span></span>

#### <a name="windows-application-packaging-project"></a><span data-ttu-id="319f1-191">Windows 應用程式封裝專案</span><span class="sxs-lookup"><span data-stu-id="319f1-191">Windows Application Packaging Project</span></span>

<span data-ttu-id="319f1-192">您可以使用 Visual Studio 中的 **Windows 應用程式封裝專案**   專案，為您的桌面應用程式產生套件。</span><span class="sxs-lookup"><span data-stu-id="319f1-192">You can use the **Windows Application Packaging Project** project in Visual Studio to generate a package for your desktop app.</span></span> <span data-ttu-id="319f1-193">然後，您可以將該套件發佈至 Microsoft Store，或將它側載到一或多部電腦上。</span><span class="sxs-lookup"><span data-stu-id="319f1-193">Then, you can publish that package to the Microsoft Store or sideload it onto one or more PCs.</span></span>

#### <a name="msix-packaging-tool"></a><span data-ttu-id="319f1-194">MSIX 封裝工具</span><span class="sxs-lookup"><span data-stu-id="319f1-194">MSIX Packaging Tool</span></span>

<span data-ttu-id="319f1-195">MSIX 封裝工具可讓您將現有的 Win32 應用程式重新封裝成 MSIX 格式。</span><span class="sxs-lookup"><span data-stu-id="319f1-195">The MSIX Packaging Tool enables you to repackage your existing Win32 applications to the MSIX format.</span></span> <span data-ttu-id="319f1-196">它提供互動式 UI 和用於轉換的命令列，讓您能夠在不使用原始程式碼的情況下轉換應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-196">It offers both an interactive UI and a command line for conversions and gives you the ability to convert an application without having the source code.</span></span>

![MSIX 封裝工具](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a><span data-ttu-id="319f1-198">套件支援架構</span><span class="sxs-lookup"><span data-stu-id="319f1-198">Package Support Framework</span></span>

<span data-ttu-id="319f1-199">封裝支援架構是一個開放原始碼套件，可在您無法存取原始程式碼時，協助您將修正套用至現有的 Win32 應用程式，以便在 MSIX 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="319f1-199">The Package Support Framework is an open-source kit that helps you apply fixes to your existing Win32 application when you don't have access to the source code, so that it can run in an MSIX container.</span></span> <span data-ttu-id="319f1-200">套件支援架構有助於讓應用程式遵循最新執行階段環境的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="319f1-200">The Package Support Framework helps your application follow the best practices of the modern runtime environment.</span></span>

#### <a name="app-installer"></a><span data-ttu-id="319f1-201">應用程式安裝程式</span><span class="sxs-lookup"><span data-stu-id="319f1-201">App Installer</span></span>

<span data-ttu-id="319f1-202">應用程式安裝程式可讓您按兩下應用程式套件，以安裝 Windows 10 應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-202">App Installer allows Windows 10 apps to be installed by double-clicking the app package.</span></span> <span data-ttu-id="319f1-203">這表示使用者不需要使用 PowerShell 或其他開發人員工具來部署 Windows 10 應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-203">This means that users don't need to use PowerShell or other developer tools to deploy Windows 10 apps.</span></span> <span data-ttu-id="319f1-204">應用程式安裝程式也可以從網頁、選用套件及相關集合中安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-204">The App Installer can also install an app from the web, optional packages, and related sets.</span></span>

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a><span data-ttu-id="319f1-205">如何從現有的 Win32 桌面應用程式建立 MSIX 封裝</span><span class="sxs-lookup"><span data-stu-id="319f1-205">How to create an MSIX package from an existing Win32 desktop application</span></span>

<span data-ttu-id="319f1-206">讓我們逐步完成從現有的 Win32 應用程式建立 MSIX 套件的流程。</span><span class="sxs-lookup"><span data-stu-id="319f1-206">Let's go through the process to create an MSIX package from an existing Win32 application.</span></span> <span data-ttu-id="319f1-207">在此範例中，我們將使用 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-207">In this example, we'll use a Windows Forms app.</span></span>

<span data-ttu-id="319f1-208">若要開始，請將新專案新增至您的方案，選取 Windows 應用程式封裝專案，並為其命名。</span><span class="sxs-lookup"><span data-stu-id="319f1-208">To start, add a new project to your solution, select the Windows Application Packaging Project, and give it a name.</span></span>

![加入新的 Windows 應用程式封裝專案](./media/deploy-modern-applications/add-packaging-project.png)

<span data-ttu-id="319f1-210">您會看到封裝專案的結構，並記下名為 [*應用程式*] 的特殊資料夾。</span><span class="sxs-lookup"><span data-stu-id="319f1-210">You'll see the structure of the packaging project and note a special folder called *Applications*.</span></span> <span data-ttu-id="319f1-211">在此資料夾中，您可以指定要包含在封裝中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-211">Inside this folder, you can specify which applications you want to include in the package.</span></span> <span data-ttu-id="319f1-212">它可以是一個以上。</span><span class="sxs-lookup"><span data-stu-id="319f1-212">It can be more than one.</span></span>

![封裝專案的結構](./media/deploy-modern-applications/packaging-project.png)

<span data-ttu-id="319f1-214">以滑鼠右鍵按一下 [*應用程式*] 資料夾，然後選取您想要從 Visual Studio 方案封裝的 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="319f1-214">Right-click on the *Applications* folder and select the Windows Forms project you want to package from the Visual Studio solution.</span></span>

![將 Windows Forms 專案新增至封裝專案](./media/deploy-modern-applications/add-winforms-project.png)

<span data-ttu-id="319f1-216">此時，您可以編譯並產生封裝，但讓我們來檢查幾件事。</span><span class="sxs-lookup"><span data-stu-id="319f1-216">At this point, you can compile and generate the package but let's examine a couple of things.</span></span> <span data-ttu-id="319f1-217">為了獲得更好的使用者體驗，Visual Studio 可以將現代化應用程式處理圖示和磚列和 [開始] 功能表的資產所需的所有視覺資產都自動產生。</span><span class="sxs-lookup"><span data-stu-id="319f1-217">To have a better user experience, Visual Studio can autogenerate all the visual assets a modern application needs to handle icons and tile assets for the tile bar and start menu.</span></span> <span data-ttu-id="319f1-218">開啟*package.appxmanifest.xml*檔案以存取資訊清單設計工具。</span><span class="sxs-lookup"><span data-stu-id="319f1-218">Open the *Package.appxmanifest* file to access the Manifest Designer.</span></span> <span data-ttu-id="319f1-219">然後按一下 [**建立**]，即可從專案中顯示的指定影像產生所有視覺資產。</span><span class="sxs-lookup"><span data-stu-id="319f1-219">You can then generate all the visual assets from a given image present on your project just by clicking **Create**.</span></span>

![Visual Studio 中的資訊清單設計工具的螢幕擷取畫面](./media/deploy-modern-applications/manifest-designer.png)

<span data-ttu-id="319f1-221">如果您開啟*package.appxmanifest.xml*檔案的程式碼，您可以看到幾個有趣的東西。</span><span class="sxs-lookup"><span data-stu-id="319f1-221">If you open the code for the *Package.appxmanifest* file, you can see a couple of interesting things.</span></span>

<span data-ttu-id="319f1-222">右邊 `<Package>` 有一個 `<Identity>` 節點。</span><span class="sxs-lookup"><span data-stu-id="319f1-222">Right under `<Package>`, there's an `<Identity>` node.</span></span> <span data-ttu-id="319f1-223">這是您的封裝應用程式即將取得其身分識別的位置，這將由 OS 管理。</span><span class="sxs-lookup"><span data-stu-id="319f1-223">This is where your packaged application is going to get its identity, which will be managed by the OS.</span></span>

![身分識別節點](./media/deploy-modern-applications/identity-node.png)

<span data-ttu-id="319f1-225">在 `<Capabilities>` 節點中，您可以找到應用程式所需的所有需求，特別注意 `<rescap:Capability Name="runFullTrust" \>` ，這會告訴 OS 在完全信任模式中執行應用程式，因為它是 Win32 應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-225">In the `<Capabilities>` node, you can find all the requirements the application needs, paying special attention to the `<rescap:Capability Name="runFullTrust" \>`, which tells the OS to run the app in full trust mode since it's a Win32 application.</span></span>

![功能節點](./media/deploy-modern-applications/capabilities-node.png)

<span data-ttu-id="319f1-227">將封裝專案設定為方案的啟始專案，然後選取 [*執行*]。</span><span class="sxs-lookup"><span data-stu-id="319f1-227">Set the packaging project as the startup project for the solution and select *Run*.</span></span> <span data-ttu-id="319f1-228">這將會：</span><span class="sxs-lookup"><span data-stu-id="319f1-228">This is going to:</span></span>

- <span data-ttu-id="319f1-229">編譯 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-229">Compile the Windows Forms application.</span></span>
- <span data-ttu-id="319f1-230">從組建結果建立 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="319f1-230">Create an MSIX package out of the build results.</span></span>
- <span data-ttu-id="319f1-231">部署封裝。</span><span class="sxs-lookup"><span data-stu-id="319f1-231">Deploy the packages.</span></span>
- <span data-ttu-id="319f1-232">將它安裝在開發電腦的本機上。</span><span class="sxs-lookup"><span data-stu-id="319f1-232">Install it locally on the development machine.</span></span>
- <span data-ttu-id="319f1-233">啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-233">Launch the app.</span></span>

![已安裝的應用程式](./media/deploy-modern-applications/our-installed-application.png)

<span data-ttu-id="319f1-235">如此一來，您就擁有全新的安裝和卸載體驗，MSIX 已完全整合到 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="319f1-235">With this, you have the clean install and uninstall experience that MSIX provides fully integrated into Windows 10.</span></span>

<span data-ttu-id="319f1-236">最後階段是關於如何將 MSIX 套件部署到另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="319f1-236">The final stage is about how you deploy the MSIX package to another machine.</span></span>

<span data-ttu-id="319f1-237">以滑鼠右鍵按一下封裝專案，選取 [**儲存**] 功能表，然後選取 [**建立應用程式套件**] 選項。</span><span class="sxs-lookup"><span data-stu-id="319f1-237">Right-click on the packaging project, select the **Store** menu, and then select the **Create App Packages** option.</span></span>

<span data-ttu-id="319f1-238">然後，您可以選擇建立要上傳至存放區的封裝，或建立用於側載的封裝。</span><span class="sxs-lookup"><span data-stu-id="319f1-238">Then, you can choose between creating a package to upload to the store or creating packages for sideloading.</span></span> <span data-ttu-id="319f1-239">在大部分的現代化案例中，您會選擇 [**我要建立側載的套件**]。</span><span class="sxs-lookup"><span data-stu-id="319f1-239">In most modernization scenarios, you'll choose **I want to create packages for sideloading**.</span></span>

![設定封裝](./media/deploy-modern-applications/configuring-packages.png)

<span data-ttu-id="319f1-241">您可以在此選取您想要設為目標的不同架構，因為您可以視需要包含多個相同的 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="319f1-241">There you can select the different architectures you want to target as you can include as many as you want into the same MSIX package.</span></span>

<span data-ttu-id="319f1-242">最後一個步驟是宣告您要部署最終安裝資產的位置。</span><span class="sxs-lookup"><span data-stu-id="319f1-242">The final step is to declare where you want to deploy the final installation assets.</span></span>

![設定更新設定](./media/deploy-modern-applications/configure-update-settings.png)

<span data-ttu-id="319f1-244">您可以選擇在企業檔案伺服器上使用共用 UNC 路徑的 web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="319f1-244">You can choose to use a web server of a shared UNC path on your enterprise file servers.</span></span> <span data-ttu-id="319f1-245">請注意設定，以指定您想要如何更新應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-245">Pay attention to the settings to specify how you want to update your application.</span></span> <span data-ttu-id="319f1-246">我們將在下一節討論應用程式更新。</span><span class="sxs-lookup"><span data-stu-id="319f1-246">We'll cover application updates in the next section.</span></span>

<span data-ttu-id="319f1-247">如需詳細的逐步指南，請參閱[使用 Visual Studio 從原始程式碼封裝桌面應用程式](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net)。</span><span class="sxs-lookup"><span data-stu-id="319f1-247">For a detailed step-by-step guide, see [Package a desktop app from source code using Visual Studio](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).</span></span>

## <a name="auto-updates-in-msix"></a><span data-ttu-id="319f1-248">MSIX 中的自動更新</span><span class="sxs-lookup"><span data-stu-id="319f1-248">Auto Updates in MSIX</span></span>

<span data-ttu-id="319f1-249">Windows Store 具有使用 Windows Update 的絕佳更新機制。</span><span class="sxs-lookup"><span data-stu-id="319f1-249">The Windows Store has a great updating mechanism using Windows Update.</span></span> <span data-ttu-id="319f1-250">在大部分的企業案例中，您不會使用存放區來散發您的桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-250">In most enterprise scenarios, you don't use the Store to distribute your desktop apps.</span></span> <span data-ttu-id="319f1-251">因此，您需要類似的方式來設定應用程式的更新，並將其提取給您的使用者。</span><span class="sxs-lookup"><span data-stu-id="319f1-251">So, you need a similar way to configure updates for your application and pull them to your users.</span></span>

<span data-ttu-id="319f1-252">使用 Windows 10 功能和 MSIX 套件的組合，您可以為使用者提供絕佳的更新體驗。</span><span class="sxs-lookup"><span data-stu-id="319f1-252">Using a combination of Windows 10 features and MSIX packages, you can provide a great updating experience for your users.</span></span> <span data-ttu-id="319f1-253">事實上，使用者不需要是技術，但仍可從順暢的應用程式更新體驗中獲益。</span><span class="sxs-lookup"><span data-stu-id="319f1-253">In fact, the user doesn't need to be technical at all but still benefit from a seamless application update experience.</span></span>

<span data-ttu-id="319f1-254">您可以透過兩種不同的方式，設定您的更新以與使用者互動：</span><span class="sxs-lookup"><span data-stu-id="319f1-254">You can configure your updates to interact with the user in two different ways:</span></span>

- <span data-ttu-id="319f1-255">使用者提示更新： OS 會顯示一些自動產生的絕佳 UI，以通知使用者有關應用程式即將安裝的資訊。</span><span class="sxs-lookup"><span data-stu-id="319f1-255">User prompted updates: The OS shows some autogenerated nice UI to notify the user about the application is about to install.</span></span> <span data-ttu-id="319f1-256">它會根據您在安裝檔案上指定的屬性來建立此 UI。</span><span class="sxs-lookup"><span data-stu-id="319f1-256">It builds this UI based on the properties you specify on your installation files.</span></span>

- <span data-ttu-id="319f1-257">背景中的無訊息更新。</span><span class="sxs-lookup"><span data-stu-id="319f1-257">Silent updates in the background.</span></span> <span data-ttu-id="319f1-258">使用此選項時，您的使用者不需要知道更新。</span><span class="sxs-lookup"><span data-stu-id="319f1-258">With this option, your users don't need to be aware of the updates.</span></span>

<span data-ttu-id="319f1-259">您也可以設定何時要在應用程式啟動或定期執行更新。</span><span class="sxs-lookup"><span data-stu-id="319f1-259">You can also configure when you want to perform updates, when the application launches or on a regular basis.</span></span> <span data-ttu-id="319f1-260">由於有側載功能，您甚至可以在應用程式執行時取得這些更新。</span><span class="sxs-lookup"><span data-stu-id="319f1-260">Thanks to the side-loading features, you can even get these updates while the application is running.</span></span>

<span data-ttu-id="319f1-261">當您使用這種類型的部署時，會建立名為*appinstaller*的特殊檔案。</span><span class="sxs-lookup"><span data-stu-id="319f1-261">When you use this type of deployment, a special file is created called *.appinstaller*.</span></span> <span data-ttu-id="319f1-262">這個簡單的檔案包含下列區段：</span><span class="sxs-lookup"><span data-stu-id="319f1-262">This simple file contains the following sections:</span></span>

- <span data-ttu-id="319f1-263">*Appinstaller*檔案的位置</span><span class="sxs-lookup"><span data-stu-id="319f1-263">The location of the *.appinstaller* file</span></span>
- <span data-ttu-id="319f1-264">應用程式的主要 MSIX 套件屬性</span><span class="sxs-lookup"><span data-stu-id="319f1-264">The application's main MSIX package properties</span></span>
- <span data-ttu-id="319f1-265">更新行為</span><span class="sxs-lookup"><span data-stu-id="319f1-265">The update behavior</span></span>

![appinstaller 檔案](./media/deploy-modern-applications/appinstaller-file.png)

<span data-ttu-id="319f1-267">隨著此檔案的結合，Microsoft 已設計了特殊的 URL 通訊協定，可從連結啟動安裝程式：</span><span class="sxs-lookup"><span data-stu-id="319f1-267">In combination with this file, Microsoft has designed a special URL protocol to launch the installation process from a link:</span></span>

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

<span data-ttu-id="319f1-268">此通訊協定適用于所有瀏覽器，並在 Windows 10 上以絕佳的使用者體驗啟動安裝程式。</span><span class="sxs-lookup"><span data-stu-id="319f1-268">This protocol works on all browsers and launches the installation process with a great user experience on Windows 10.</span></span> <span data-ttu-id="319f1-269">由於作業系統會管理安裝程式，因此它會留意此應用程式的安裝位置，並追蹤該進程所影響的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="319f1-269">Since the OS manages the installation process, it's aware of the location this application was installed from and tracks all the files affected by the process.</span></span>

<span data-ttu-id="319f1-270">MSIX 會建立用於安裝的使用者介面，以自動顯示封裝的某些屬性。</span><span class="sxs-lookup"><span data-stu-id="319f1-270">MSIX creates a user interface for installation automatically showing some properties of the package.</span></span> <span data-ttu-id="319f1-271">這可讓每個應用程式都有常見的安裝體驗。</span><span class="sxs-lookup"><span data-stu-id="319f1-271">This allows for a common installation experience for every app.</span></span>

<span data-ttu-id="319f1-272">當您產生新的 MSIX 套件並將它移至部署伺服器之後，您只需要編輯*appinstaller*檔案來反映這些變更，主要是版本以及新 MSIX 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="319f1-272">Once you've generated the new MSIX package and moved it to the deployment server, you just have to edit the *.appinstaller* file to reflect these changes, mainly the version and the path to the new MSIX file.</span></span> <span data-ttu-id="319f1-273">下次使用者啟動應用程式時，系統會偵測到變更，並在背景下載新版本的檔案。</span><span class="sxs-lookup"><span data-stu-id="319f1-273">The next time the user launches the application, the system is going to detect the change and download the files for the new version in the background.</span></span> <span data-ttu-id="319f1-274">完成此動作時，系統會針對您的使用者，以透明的方式在新的應用程式啟動時執行安裝。</span><span class="sxs-lookup"><span data-stu-id="319f1-274">When this is done, installation will execute on new application launch transparently for your user.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="319f1-275">上一步</span><span class="sxs-lookup"><span data-stu-id="319f1-275">Previous</span></span>](example-migration-core.md)
