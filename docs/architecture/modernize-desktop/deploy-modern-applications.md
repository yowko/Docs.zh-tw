---
title: 部署現代化傳統型應用程式
description: 部署新式桌面應用程式所需知道的一切。
ms.date: 05/12/2020
ms.openlocfilehash: ba47f09b27adf270734bbfff285fe44dd4175d29
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615850"
---
# <a name="deploying-modern-desktop-applications"></a><span data-ttu-id="a4f2e-103">部署現代化傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="a4f2e-103">Deploying Modern Desktop Applications</span></span>

<span data-ttu-id="a4f2e-104">當您開發桌面應用程式時，要考慮的一件事就是您的應用程式要如何封裝及部署到使用者的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-104">When you develop desktop applications, one thing to consider is how your application is going to be packaged and deployed to the users' machines.</span></span> <span data-ttu-id="a4f2e-105">封裝、部署和安裝的問題是，它通常會落在 IT 專業人員的範圍內，而不是與開發人員在意不同的事物。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-105">The problem with packaging, deployment, and installation is that it usually falls under the umbrella of the IT professionals, who care about different things than developers.</span></span>

<span data-ttu-id="a4f2e-106">這幾天，我們全都熟悉 DevOps 的概念，讓開發人員和 IT 專業人員能夠密切合作將應用程式移至生產環境。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-106">These days, we're all familiar with the DevOps concept, where developers and IT Pros work closely to move applications to their production environments.</span></span> <span data-ttu-id="a4f2e-107">但是，如果您在桌上型電腦上有10年的時間，您可能會看到下列案例。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-107">But if you've been in the desktop battle for more than 10 years, you might have seen the following story.</span></span> <span data-ttu-id="a4f2e-108">開發人員團隊合作，以符合專案期限。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-108">A team of developers works together hard to meet the project deadlines.</span></span> <span data-ttu-id="a4f2e-109">商務人員緊張，因為他們需要在許多使用者的電腦上工作，才能執行公司。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-109">Business people are nervous since they need the system working on many user's machines to run the company.</span></span> <span data-ttu-id="a4f2e-110">在「D 天」，專案經理會向每位開發人員檢查其程式碼是否正常運作，而且一切都沒問題，因此可以寄送。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-110">On "D-Day", the project manager checks with every developer that their code is working well and that everything is fine, so they can ship.</span></span> <span data-ttu-id="a4f2e-111">然後，套件小組會產生應用程式的安裝程式、將其散發給每個使用者電腦，以及一組測試使用者執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-111">Then, the package team comes in generating the setup for the app, distribute it to every user machine and a set of test users run the application.</span></span> <span data-ttu-id="a4f2e-112">他們會嘗試，因為在顯示任何 UI 之前，應用程式會擲回一個例外狀況，指出「物件 ~ 失敗」的方法。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-112">Well, they try, because before showing any UI, the application throws an exception that says "Method ~ of object ~ failed".</span></span> <span data-ttu-id="a4f2e-113">緊急情況會開始流經空氣，並將簡短的調查點帶到已引進協力廠商控制項的年輕開發人員，也就是「在開發電腦上工作」。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-113">Panic starts flowing through the air and a brief investigation points to a young and tired developer that has introduced a third-party control, that certainly "worked on the dev machine".</span></span>

<span data-ttu-id="a4f2e-114">傳統上，安裝桌面應用程式有兩個主要原因：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-114">Installing desktop applications have traditionally been a nightmare for two main reasons:</span></span>

- <span data-ttu-id="a4f2e-115">缺乏開發和 IT 小組之間的密切合作文化。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-115">Lack of close collaboration culture between dev and IT teams.</span></span>
- <span data-ttu-id="a4f2e-116">缺乏穩固的封裝和部署技術可建立。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-116">Lack of a solid packaging and deploying technology we can build upon.</span></span>

<span data-ttu-id="a4f2e-117">事實上，我們一直以來都致歉您安裝了應用程式，因為：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-117">In fact, we've been living with the fact that sometimes you regret that you installed an app because:</span></span>

- <span data-ttu-id="a4f2e-118">它最後會對您的電腦造成一些不想要的副作用。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-118">It ends up having some undesired side effects on your machine.</span></span>
- <span data-ttu-id="a4f2e-119">某些先前安裝的應用程式會停止運作。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-119">Some applications that were previously installed stop working.</span></span>

<span data-ttu-id="a4f2e-120">此外，您也無法藉由卸載應用程式，將系統還原為其原始狀態。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-120">Additionally, you can't just restore the system to its original state by uninstalling the app.</span></span> <span data-ttu-id="a4f2e-121">我們習慣在這種情況下，我們創造了「DLL Hell」或「Winrot」等詞彙。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-121">We're so used to live this situation that we've coined terms like "DLL Hell" or "Winrot".</span></span>

<span data-ttu-id="a4f2e-122">在本章中，我們將討論 MSIX。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-122">In this chapter, we'll talk about MSIX.</span></span> <span data-ttu-id="a4f2e-123">MSIX 是 Microsoft 的全新技術，其會嘗試抓住最優秀的技術，為未來的封裝技術提供穩固的基礎。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-123">MSIX is the brand-new technology from Microsoft that tries to capture the best of previous technologies to provide a solid foundation for the packaging technology of the future.</span></span>

<span data-ttu-id="a4f2e-124">封裝技術與現代化有何用途？</span><span class="sxs-lookup"><span data-stu-id="a4f2e-124">What does a packaging technology have to do with modernization?</span></span> <span data-ttu-id="a4f2e-125">其實，封裝是企業 IT 的基礎，在那裡投資了許多資金。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-125">Well, it turns out that packaging is fundamental for the enterprise IT with lots of money invested there.</span></span> <span data-ttu-id="a4f2e-126">現代化不僅與使用最新的技術有關。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-126">Modernization isn't only related to using the latest technologies.</span></span> <span data-ttu-id="a4f2e-127">這也與您的公司將功能交付給用戶端之前，縮短了商務需求的定義時間。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-127">It's also related to reducing time to market from the moment a business requirement is defined until your company delivers the feature to your client.</span></span>

## <a name="the-modern-application-lifecycle"></a><span data-ttu-id="a4f2e-128">新式應用程式生命週期</span><span class="sxs-lookup"><span data-stu-id="a4f2e-128">The modern application lifecycle</span></span>

<span data-ttu-id="a4f2e-129">現今，開發人員會撰寫並建立應用程式的程式碼，然後將產生的資產傳遞給 IT 專業人員。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-129">Today, developers write and build the code for an app and then pass the generated assets to the IT Pros.</span></span> <span data-ttu-id="a4f2e-130">然後，IT 專業人員會重新設定應用程式，並將它重新封裝（通常是在 MSI 中，或更新的應用程式-V 封裝格式）。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-130">Then, the IT Pros reconfigure the app and repackage it, typically in an MSI or more recently in an App-V packaging format.</span></span> <span data-ttu-id="a4f2e-131">然後會透過不同的通道和工具來部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-131">The app is then deployed through different channels and tools.</span></span> <span data-ttu-id="a4f2e-132">這種方法的其中一個主要問題，通常稱為「封裝 paralysis」。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-132">One of the main problems with this approach is commonly known as "packaging paralysis".</span></span> <span data-ttu-id="a4f2e-133">問題在於，每次有應用程式更新或作業系統更新時，此週期都會重複。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-133">The problem is that this cycle repeats every time there's an app update or an OS update.</span></span>

<span data-ttu-id="a4f2e-134">您可以看到此程式反映在下圖中：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-134">You can see the process reflected on the following picture:</span></span>

![顯示新式 IT 生命週期的圖表](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

<span data-ttu-id="a4f2e-136">公司需要將此封裝週期分成三個獨立週期的方法：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-136">Companies need a way to break this packaging cycle into three independent cycles:</span></span>

- <span data-ttu-id="a4f2e-137">OS 更新</span><span class="sxs-lookup"><span data-stu-id="a4f2e-137">OS updates</span></span>
- <span data-ttu-id="a4f2e-138">應用程式更新</span><span class="sxs-lookup"><span data-stu-id="a4f2e-138">Application updates</span></span>
- <span data-ttu-id="a4f2e-139">自訂</span><span class="sxs-lookup"><span data-stu-id="a4f2e-139">Customization</span></span>

![顯示新式 IT 良性週期的圖表](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

<span data-ttu-id="a4f2e-141">上圖顯示您可以：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-141">The previous diagram shows that you can:</span></span>

- <span data-ttu-id="a4f2e-142">更新基礎作業系統，而不需要重新封裝您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-142">Update the underlying OS without having to repackage your apps.</span></span>
- <span data-ttu-id="a4f2e-143">從中進行自訂，而不需要重新封裝原始開發人員套件。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-143">Enable customizations from IT without the need to repackage the original developer package.</span></span>

<span data-ttu-id="a4f2e-144">這項最新的改變將引導我們到新式和新式 IT 生命週期，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-144">This radical change leads us to the new and modern IT lifecycle as shown in the following picture:</span></span>

![顯示使用 Microsoft 工具之應用程式生命週期的圖表](./media/deploy-modern-applications/microsoft-it-tools.png)

<span data-ttu-id="a4f2e-146">開發人員會建立應用程式，並產生可供 IT 專業人員使用並設定的 MSIX 套件，而不需要重新封裝。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-146">Developers create the app and generate an MSIX package that IT Pros can consume and configure without the need of repackaging.</span></span> <span data-ttu-id="a4f2e-147">除了 MSIX 技術，Microsoft 還建立了可讓 IT 自訂和設定套件的工具，而不需要重新封裝。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-147">Along with the MSIX technology, Microsoft has created tools to allow IT to customize and configure packages without repackaging.</span></span>

## <a name="msix-the-next-generation-of-deployment"></a><span data-ttu-id="a4f2e-148">MSIX：新一代的部署</span><span class="sxs-lookup"><span data-stu-id="a4f2e-148">MSIX: The next generation of deployment</span></span>

<span data-ttu-id="a4f2e-149">在 MSIX 之前，有數種封裝技術可供使用，像是安裝程式、MSI、ClickOnce、App-v 和腳本。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-149">Before MSIX, there were several packaging technologies available like setup wizards, MSI, ClickOnce, App-V, and scripting.</span></span> <span data-ttu-id="a4f2e-150">這兩種技術都有自己的優勢，而 Microsoft 決定挑選最適合建立 MSIX。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-150">Each of these technologies has their own strengths and Microsoft has decided to pick the best of all to build MSIX.</span></span> <span data-ttu-id="a4f2e-151">MSIX 是以這些現有技術的基礎為基礎，可挑選各項技術的最佳基礎：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-151">MSIX is built on the foundations of these existing technologies picking the best of each:</span></span>

- <span data-ttu-id="a4f2e-152">App-v = \> 容器化</span><span class="sxs-lookup"><span data-stu-id="a4f2e-152">App-V =\> Containerization</span></span>
- <span data-ttu-id="a4f2e-153">ClickOnce = \> 自動更新</span><span class="sxs-lookup"><span data-stu-id="a4f2e-153">ClickOnce =\> Auto updating</span></span>
- <span data-ttu-id="a4f2e-154">MSI = \> 容易散發</span><span class="sxs-lookup"><span data-stu-id="a4f2e-154">MSI =\> Easy to distribute</span></span>

<span data-ttu-id="a4f2e-155">透過 MSIX，您可以取得一項安裝程式技術，其中包含所有這些功能。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-155">With MSIX, you get one installer technology with all these features.</span></span>

![顯示影響組建 MSIX 之不同技術的圖表](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a><span data-ttu-id="a4f2e-157">MSIX 的優點</span><span class="sxs-lookup"><span data-stu-id="a4f2e-157">Benefits of MSIX</span></span>

#### <a name="never-regret-installing-an-app"></a><span data-ttu-id="a4f2e-158">永不致歉安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="a4f2e-158">Never regret installing an app</span></span>

<span data-ttu-id="a4f2e-159">MSIX 提供可預測、可靠且安全的部署。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-159">MSIX provides a predictable, reliable, and safe deployment.</span></span> <span data-ttu-id="a4f2e-160">封裝資訊清單中包含的宣告方法可讓 OS 追蹤應用程式所需的每個資產。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-160">The declarative method contained in the package manifest lets the OS keep track of every asset your application needs.</span></span> <span data-ttu-id="a4f2e-161">它也提供真正的全新卸載且沒有副作用。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-161">It also provides a true clean uninstall with no side effects.</span></span>

#### <a name="disk-space-optimization"></a><span data-ttu-id="a4f2e-162">磁碟空間優化</span><span class="sxs-lookup"><span data-stu-id="a4f2e-162">Disk space optimization</span></span>

<span data-ttu-id="a4f2e-163">MSIX 已優化，可減少應用程式對使用者電腦磁碟空間的使用量。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-163">MSIX is optimized to reduce the footprint that an application has on the user's machine disk space.</span></span> <span data-ttu-id="a4f2e-164">它會建立檔案的單一實例存放區。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-164">It creates a single instance storage of your files.</span></span> <span data-ttu-id="a4f2e-165">也就是說，如果您有兩個具有相同 DLL 的不同套件，則不會安裝 DLL 兩次。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-165">That is, if you have two different packages with the same DLL, the DLL isn't installed twice.</span></span> <span data-ttu-id="a4f2e-166">平臺會處理這個問題，因為它知道特定應用程式所安裝的所有檔案都有其宣告式本質。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-166">The platform takes care of that problem because it knows all the files that a particular app installed thanks to its declarative nature.</span></span> <span data-ttu-id="a4f2e-167">它也可讓您將不同版本的 DLL 並存運作。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-167">It also allows you to have different versions of a DLL working side by side.</span></span>

<span data-ttu-id="a4f2e-168">使用資源套件時，您可以輕鬆地建立多語系應用程式，而 OS 會負責安裝使用的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-168">With the use of resource packages, you can easily create multilingual apps and the OS takes care of installing the ones that are used.</span></span>

#### <a name="network-optimization"></a><span data-ttu-id="a4f2e-169">網路優化</span><span class="sxs-lookup"><span data-stu-id="a4f2e-169">Network optimization</span></span>

<span data-ttu-id="a4f2e-170">MSIX 會偵測位元組區塊層級的檔案差異，並啟用稱為差異更新的功能。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-170">MSIX detects the differences on the files at the byte block level enabling a feature called differential updates.</span></span> <span data-ttu-id="a4f2e-171">這表示，只會在應用程式更新上下載已更新的位元組區塊。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-171">What this means is that only the updated byte blocks are downloaded on application updates.</span></span>

![顯示 MSIX 如何管理差異更新的圖表](./media/deploy-modern-applications/msix-managing-updates.png)

<span data-ttu-id="a4f2e-173">使用串流安裝時，使用者可以快速開始處理您的應用程式，而應用程式的其他部分則會在背景下載。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-173">With streaming installation, the user can quickly start working on your application while other parts of the app are downloaded on the background.</span></span> <span data-ttu-id="a4f2e-174">這項功能可為您的使用者提供吸引人的體驗。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-174">This feature contributes to an engaging experience for your users.</span></span>

<span data-ttu-id="a4f2e-175">使用選擇性套件功能時，您可以在應用程式部署上達成元件化，以便在需要時下載。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-175">With the optional packages feature, you achieve componentization on your app deployment, so you can download them when needed.</span></span>

#### <a name="simple-packaging-and-deployment"></a><span data-ttu-id="a4f2e-176">簡單的封裝和部署</span><span class="sxs-lookup"><span data-stu-id="a4f2e-176">Simple packaging and deployment</span></span>

<span data-ttu-id="a4f2e-177">AppManifest 會宣告版本控制、裝置目標，並以標準方式針對每個應用程式進行識別。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-177">The AppManifest declares the versioning, device targeting and identify in a standard way for every application.</span></span> <span data-ttu-id="a4f2e-178">它也提供一種方式來簽署您的資產，以提供穩固的安全性基礎。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-178">It also provides a way to sign your assets providing a solid security foundation.</span></span>

#### <a name="os-managed"></a><span data-ttu-id="a4f2e-179">作業系統管理</span><span class="sxs-lookup"><span data-stu-id="a4f2e-179">OS managed</span></span>

<span data-ttu-id="a4f2e-180">作業系統會處理安裝、更新和移除應用程式的所有進程。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-180">The OS handles all the processes for installing, updating, and removing an application.</span></span> <span data-ttu-id="a4f2e-181">應用程式會針對每個使用者安裝，但只會下載一次，將磁片使用量降到最低。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-181">Applications are installed per user but downloaded only once, minimizing the disk footprint.</span></span> <span data-ttu-id="a4f2e-182">Microsoft 正在努力提供 Windows 7 上的 MSIX 經驗。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-182">Microsoft is working on providing the MSIX experience also on Windows 7.</span></span>

#### <a name="windows-provides-integrity-for-the-app"></a><span data-ttu-id="a4f2e-183">Windows 提供應用程式的完整性</span><span class="sxs-lookup"><span data-stu-id="a4f2e-183">Windows provides integrity for the app</span></span>

<span data-ttu-id="a4f2e-184">使用數位簽章時，您可以確保不會從不受信任的來源安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-184">With the use of digital signatures, you can guarantee that you don't install an application from untrusted sources.</span></span> <span data-ttu-id="a4f2e-185">MSIX 也會防止篡改，因為：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-185">MSIX also prevents tampering because:</span></span>

- <span data-ttu-id="a4f2e-186">它會保留檔雜湊的記錄。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-186">It keeps a record of file hashes.</span></span>
- <span data-ttu-id="a4f2e-187">它會偵測在安裝之後是否已修改檔案。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-187">It detects if a file has been modified after installation.</span></span>

#### <a name="works-for-the-entire-app-catalog"></a><span data-ttu-id="a4f2e-188">適用于整個應用程式類別目錄</span><span class="sxs-lookup"><span data-stu-id="a4f2e-188">Works for the entire App Catalog</span></span>

<span data-ttu-id="a4f2e-189">MSIX 的其中一個最酷事項，就是適用于整個應用程式類別目錄、Windows Forms、WPF、MFC/ATL、Delphi，即使您想要執行 xCopy 部署、ClickOnce 或前往存放區，也可以使用相同的 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-189">One of the coolest things about MSIX is that it works for the entire application catalog, Windows Forms, WPF, MFC/ATL, Delphi, even if you want to do xCopy deployment, ClickOnce, or going to the Store, you can use the same MSIX package.</span></span>

### <a name="tools"></a><span data-ttu-id="a4f2e-190">工具</span><span class="sxs-lookup"><span data-stu-id="a4f2e-190">Tools</span></span>

#### <a name="windows-application-packaging-project"></a><span data-ttu-id="a4f2e-191">Windows 應用程式封裝專案</span><span class="sxs-lookup"><span data-stu-id="a4f2e-191">Windows Application Packaging Project</span></span>

<span data-ttu-id="a4f2e-192">您可以使用 Visual Studio 中的 **Windows 應用程式封裝專案**，為傳統型應用程式產生套件。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-192">You can use the **Windows Application Packaging Project** project in Visual Studio to generate a package for your desktop app.</span></span> <span data-ttu-id="a4f2e-193">然後，您可以將該套件發佈至 Microsoft Store 或側載到一或多部電腦上。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-193">Then, you can publish that package to the Microsoft Store or sideload it onto one or more PCs.</span></span>

#### <a name="msix-packaging-tool"></a><span data-ttu-id="a4f2e-194">MSIX 封裝工具</span><span class="sxs-lookup"><span data-stu-id="a4f2e-194">MSIX Packaging Tool</span></span>

<span data-ttu-id="a4f2e-195">MSIX 封裝工具可讓您將現有的 Win32 應用程式重新封裝成 MSIX 格式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-195">The MSIX Packaging Tool enables you to repackage your existing Win32 applications to the MSIX format.</span></span> <span data-ttu-id="a4f2e-196">它同時提供互動式 UI 和命令列以進行轉換，讓您能夠在不需要原始程式碼的情況下轉換應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-196">It offers both an interactive UI and a command line for conversions and gives you the ability to convert an application without having the source code.</span></span>

![MSIX 封裝工具](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a><span data-ttu-id="a4f2e-198">套件支援架構</span><span class="sxs-lookup"><span data-stu-id="a4f2e-198">Package Support Framework</span></span>

<span data-ttu-id="a4f2e-199">套件支援架構是開放原始碼套件，可在您沒有原始程式碼的存取權時，協助您將修正套用至現有的 Win32 應用程式，讓它可以在 MSIX 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-199">The Package Support Framework is an open-source kit that helps you apply fixes to your existing Win32 application when you don't have access to the source code, so that it can run in an MSIX container.</span></span> <span data-ttu-id="a4f2e-200">套件支援架構有助於讓應用程式遵循最新執行階段環境的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-200">The Package Support Framework helps your application follow the best practices of the modern runtime environment.</span></span>

#### <a name="app-installer"></a><span data-ttu-id="a4f2e-201">應用程式安裝程式</span><span class="sxs-lookup"><span data-stu-id="a4f2e-201">App Installer</span></span>

<span data-ttu-id="a4f2e-202">應用程式安裝程式可以按兩下應用程式套件，以允許安裝 Windows 10 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-202">App Installer allows Windows 10 apps to be installed by double-clicking the app package.</span></span> <span data-ttu-id="a4f2e-203">這表示使用者不需要使用 PowerShell 或其他開發人員工具來部署 Windows 10 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-203">This means that users don't need to use PowerShell or other developer tools to deploy Windows 10 apps.</span></span> <span data-ttu-id="a4f2e-204">應用程式安裝程式也可以從網頁、選用套件及相關集合中安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-204">The App Installer can also install an app from the web, optional packages, and related sets.</span></span>

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a><span data-ttu-id="a4f2e-205">如何從現有的 Win32 桌面應用程式建立 MSIX 套件</span><span class="sxs-lookup"><span data-stu-id="a4f2e-205">How to create an MSIX package from an existing Win32 desktop application</span></span>

<span data-ttu-id="a4f2e-206">讓我們逐一完成從現有的 Win32 應用程式建立 MSIX 套件的程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-206">Let's go through the process to create an MSIX package from an existing Win32 application.</span></span> <span data-ttu-id="a4f2e-207">在此範例中，我們將使用 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-207">In this example, we'll use a Windows Forms app.</span></span>

<span data-ttu-id="a4f2e-208">若要開始，請將新的專案新增至您的方案，選取 Windows 應用程式封裝專案，並為其命名。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-208">To start, add a new project to your solution, select the Windows Application Packaging Project, and give it a name.</span></span>

![加入新的 Windows 應用程式封裝專案](./media/deploy-modern-applications/add-packaging-project.png)

<span data-ttu-id="a4f2e-210">您將會看到封裝專案的結構，並記下稱為「 *應用程式*」的特殊資料夾。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-210">You'll see the structure of the packaging project and note a special folder called *Applications*.</span></span> <span data-ttu-id="a4f2e-211">在此資料夾內，您可以指定要包含在封裝中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-211">Inside this folder, you can specify which applications you want to include in the package.</span></span> <span data-ttu-id="a4f2e-212">它可以是一個以上。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-212">It can be more than one.</span></span>

![封裝專案的結構](./media/deploy-modern-applications/packaging-project.png)

<span data-ttu-id="a4f2e-214">在 [ *應用程式* ] 資料夾上按一下滑鼠右鍵，然後從 Visual Studio 方案中選取您要封裝的 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-214">Right-click on the *Applications* folder and select the Windows Forms project you want to package from the Visual Studio solution.</span></span>

![將 Windows Forms 專案新增至封裝專案](./media/deploy-modern-applications/add-winforms-project.png)

<span data-ttu-id="a4f2e-216">至此，您可以編譯和產生封裝，但讓我們來檢驗一下一些東西。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-216">At this point, you can compile and generate the package but let's examine a couple of things.</span></span> <span data-ttu-id="a4f2e-217">為了獲得更好的使用者體驗，Visual Studio 可以自動產生新式應用程式所需的所有視覺資產，以處理磚列和 [開始] 功能表的圖示和磚資產。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-217">To have a better user experience, Visual Studio can autogenerate all the visual assets a modern application needs to handle icons and tile assets for the tile bar and start menu.</span></span> <span data-ttu-id="a4f2e-218">開啟 *package.appxmanifest* 檔案以存取資訊清單設計工具。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-218">Open the *Package.appxmanifest* file to access the Manifest Designer.</span></span> <span data-ttu-id="a4f2e-219">然後，只要按一下 [ **建立**]，就可以從專案上的指定影像產生所有視覺資產。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-219">You can then generate all the visual assets from a given image present on your project just by clicking **Create**.</span></span>

![Visual Studio 中資訊清單設計工具的螢幕擷取畫面](./media/deploy-modern-applications/manifest-designer.png)

<span data-ttu-id="a4f2e-221">如果您開啟 *package.appxmanifest* 檔案的程式碼，您可以看到幾個有趣的事情。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-221">If you open the code for the *Package.appxmanifest* file, you can see a couple of interesting things.</span></span>

<span data-ttu-id="a4f2e-222">右側 `<Package>` 有一個 `<Identity>` 節點。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-222">Right under `<Package>`, there's an `<Identity>` node.</span></span> <span data-ttu-id="a4f2e-223">這是您的已封裝應用程式要取得其身分識別的位置，這會由作業系統管理。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-223">This is where your packaged application is going to get its identity, which will be managed by the OS.</span></span>

![身分識別節點](./media/deploy-modern-applications/identity-node.png)

<span data-ttu-id="a4f2e-225">在 `<Capabilities>` 節點中，您可以找到應用程式所需的所有需求，特別注意，它會 `<rescap:Capability Name="runFullTrust" \>` 告訴 OS 以完全信任模式執行應用程式，因為它是 Win32 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-225">In the `<Capabilities>` node, you can find all the requirements the application needs, paying special attention to the `<rescap:Capability Name="runFullTrust" \>`, which tells the OS to run the app in full trust mode since it's a Win32 application.</span></span>

![功能節點](./media/deploy-modern-applications/capabilities-node.png)

<span data-ttu-id="a4f2e-227">將封裝專案設定為方案的啟始專案，然後選取 [ *執行*]。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-227">Set the packaging project as the startup project for the solution and select *Run*.</span></span> <span data-ttu-id="a4f2e-228">這將會：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-228">This is going to:</span></span>

- <span data-ttu-id="a4f2e-229">編譯 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-229">Compile the Windows Forms application.</span></span>
- <span data-ttu-id="a4f2e-230">從組建結果建立 MSIX 套件。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-230">Create an MSIX package out of the build results.</span></span>
- <span data-ttu-id="a4f2e-231">部署套件。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-231">Deploy the packages.</span></span>
- <span data-ttu-id="a4f2e-232">將它安裝在開發電腦的本機上。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-232">Install it locally on the development machine.</span></span>
- <span data-ttu-id="a4f2e-233">啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-233">Launch the app.</span></span>

![我們已安裝的應用程式](./media/deploy-modern-applications/our-installed-application.png)

<span data-ttu-id="a4f2e-235">透過這種方式，您可以使用 MSIX 完全整合到 Windows 10 的全新安裝和卸載體驗。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-235">With this, you have the clean install and uninstall experience that MSIX provides fully integrated into Windows 10.</span></span>

<span data-ttu-id="a4f2e-236">最後一個階段是關於如何將 MSIX 封裝部署到另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-236">The final stage is about how you deploy the MSIX package to another machine.</span></span>

<span data-ttu-id="a4f2e-237">以滑鼠右鍵按一下封裝專案，選取 [ **儲存** ] 功能表，然後選取 [ **建立應用程式套件** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-237">Right-click on the packaging project, select the **Store** menu, and then select the **Create App Packages** option.</span></span>

<span data-ttu-id="a4f2e-238">然後，您可以選擇建立要上傳至存放區的封裝，或建立用於側載的封裝。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-238">Then, you can choose between creating a package to upload to the store or creating packages for sideloading.</span></span> <span data-ttu-id="a4f2e-239">在大部分的現代化案例中，您會選擇要 **建立側載的套件**。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-239">In most modernization scenarios, you'll choose **I want to create packages for sideloading**.</span></span>

![設定套件](./media/deploy-modern-applications/configuring-packages.png)

<span data-ttu-id="a4f2e-241">您可以選取想要作為目標的不同架構，因為您可以將任意數量包含在相同的 MSIX 套件中。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-241">There you can select the different architectures you want to target as you can include as many as you want into the same MSIX package.</span></span>

<span data-ttu-id="a4f2e-242">最後一個步驟是宣告您想要部署最終安裝資產的位置。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-242">The final step is to declare where you want to deploy the final installation assets.</span></span>

![設定更新設定](./media/deploy-modern-applications/configure-update-settings.png)

<span data-ttu-id="a4f2e-244">您可以選擇在企業檔案伺服器上使用共用 UNC 路徑的 web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-244">You can choose to use a web server of a shared UNC path on your enterprise file servers.</span></span> <span data-ttu-id="a4f2e-245">請注意這些設定，以指定您要如何更新應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-245">Pay attention to the settings to specify how you want to update your application.</span></span> <span data-ttu-id="a4f2e-246">我們將在下一節討論應用程式更新。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-246">We'll cover application updates in the next section.</span></span>

<span data-ttu-id="a4f2e-247">如需詳細的逐步指南，請參閱 [使用 Visual Studio 從原始程式碼封裝桌面應用程式](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net)。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-247">For a detailed step-by-step guide, see [Package a desktop app from source code using Visual Studio](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).</span></span>

## <a name="auto-updates-in-msix"></a><span data-ttu-id="a4f2e-248">MSIX 中的自動更新</span><span class="sxs-lookup"><span data-stu-id="a4f2e-248">Auto Updates in MSIX</span></span>

<span data-ttu-id="a4f2e-249">Windows 儲存區具有使用 Windows Update 的絕佳更新機制。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-249">The Windows Store has a great updating mechanism using Windows Update.</span></span> <span data-ttu-id="a4f2e-250">在大部分的企業案例中，您不會使用存放區來散發您的桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-250">In most enterprise scenarios, you don't use the Store to distribute your desktop apps.</span></span> <span data-ttu-id="a4f2e-251">因此，您需要類似的方式來設定應用程式的更新，並將其提取給您的使用者。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-251">So, you need a similar way to configure updates for your application and pull them to your users.</span></span>

<span data-ttu-id="a4f2e-252">使用 Windows 10 功能和 MSIX 套件的組合，您可以為您的使用者提供絕佳的更新體驗。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-252">Using a combination of Windows 10 features and MSIX packages, you can provide a great updating experience for your users.</span></span> <span data-ttu-id="a4f2e-253">事實上，使用者根本不需要具備技術技術，但仍可從流暢的應用程式更新體驗中獲益。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-253">In fact, the user doesn't need to be technical at all but still benefit from a seamless application update experience.</span></span>

<span data-ttu-id="a4f2e-254">您可以使用兩種不同的方式來設定更新與使用者互動：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-254">You can configure your updates to interact with the user in two different ways:</span></span>

- <span data-ttu-id="a4f2e-255">使用者提示更新：作業系統會顯示一些自動產生的絕佳 UI，以通知使用者即將安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-255">User prompted updates: The OS shows some autogenerated nice UI to notify the user about the application is about to install.</span></span> <span data-ttu-id="a4f2e-256">它會根據您在安裝檔案中指定的屬性來建立這個 UI。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-256">It builds this UI based on the properties you specify on your installation files.</span></span>

- <span data-ttu-id="a4f2e-257">背景中的無訊息更新。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-257">Silent updates in the background.</span></span> <span data-ttu-id="a4f2e-258">使用這個選項時，您的使用者不需要察覺更新。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-258">With this option, your users don't need to be aware of the updates.</span></span>

<span data-ttu-id="a4f2e-259">您也可以設定當應用程式啟動或定期執行更新時，您要執行更新的時間。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-259">You can also configure when you want to perform updates, when the application launches or on a regular basis.</span></span> <span data-ttu-id="a4f2e-260">由於有側載功能，您甚至可以在應用程式執行時取得這些更新。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-260">Thanks to the side-loading features, you can even get these updates while the application is running.</span></span>

<span data-ttu-id="a4f2e-261">當您使用此類部署時，會建立一個稱為 *appinstaller* 的特殊檔案。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-261">When you use this type of deployment, a special file is created called *.appinstaller*.</span></span> <span data-ttu-id="a4f2e-262">這個簡單的檔案包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-262">This simple file contains the following sections:</span></span>

- <span data-ttu-id="a4f2e-263">*Appinstaller* 檔案的位置</span><span class="sxs-lookup"><span data-stu-id="a4f2e-263">The location of the *.appinstaller* file</span></span>
- <span data-ttu-id="a4f2e-264">應用程式的主要 MSIX 套件屬性</span><span class="sxs-lookup"><span data-stu-id="a4f2e-264">The application's main MSIX package properties</span></span>
- <span data-ttu-id="a4f2e-265">更新行為</span><span class="sxs-lookup"><span data-stu-id="a4f2e-265">The update behavior</span></span>

![appinstaller 檔案](./media/deploy-modern-applications/appinstaller-file.png)

<span data-ttu-id="a4f2e-267">隨著這個檔案的組合，Microsoft 已經設計了一個特殊的 URL 通訊協定，從連結啟動安裝程式：</span><span class="sxs-lookup"><span data-stu-id="a4f2e-267">In combination with this file, Microsoft has designed a special URL protocol to launch the installation process from a link:</span></span>

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

<span data-ttu-id="a4f2e-268">此通訊協定適用于所有瀏覽器，並在 Windows 10 上以絕佳的使用者體驗啟動安裝程式。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-268">This protocol works on all browsers and launches the installation process with a great user experience on Windows 10.</span></span> <span data-ttu-id="a4f2e-269">由於作業系統會管理安裝程式，因此它會知道此應用程式的安裝位置，並且會追蹤進程所影響的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-269">Since the OS manages the installation process, it's aware of the location this application was installed from and tracks all the files affected by the process.</span></span>

<span data-ttu-id="a4f2e-270">MSIX 會建立用於安裝的使用者介面，以自動顯示封裝的某些屬性。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-270">MSIX creates a user interface for installation automatically showing some properties of the package.</span></span> <span data-ttu-id="a4f2e-271">這可讓您針對每個應用程式提供常見的安裝體驗。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-271">This allows for a common installation experience for every app.</span></span>

<span data-ttu-id="a4f2e-272">當您產生新的 MSIX 套件，並將它移至部署伺服器之後，您只需要編輯 *appinstaller* 檔案來反映這些變更，主要是版本以及新 MSIX 檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-272">Once you've generated the new MSIX package and moved it to the deployment server, you just have to edit the *.appinstaller* file to reflect these changes, mainly the version and the path to the new MSIX file.</span></span> <span data-ttu-id="a4f2e-273">使用者下一次啟動應用程式時，系統會偵測到變更，並在背景下載新版本的檔案。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-273">The next time the user launches the application, the system is going to detect the change and download the files for the new version in the background.</span></span> <span data-ttu-id="a4f2e-274">完成這項操作時，系統會為您的使用者以透明的方式在新的應用程式啟動時執行安裝。</span><span class="sxs-lookup"><span data-stu-id="a4f2e-274">When this is done, installation will execute on new application launch transparently for your user.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a4f2e-275">[[上一步]](example-migration.md)</span><span class="sxs-lookup"><span data-stu-id="a4f2e-275">[Previous](example-migration.md)</span></span>
