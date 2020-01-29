---
title: 安裝當地語系化的 IntelliSense 檔案
description: 了解如何設定開發電腦，以在 Visual Studio 中使用 .NET Core 專案的當地語系化 IntelliSense 檔案。
ms.date: 01/23/2020
ms.openlocfilehash: 58b462507edf953a6c28aadbb9e3239a5cbe05b2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733646"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="8207e-103">如何安裝 .NET Core 的當地語系化 IntelliSense 檔案</span><span class="sxs-lookup"><span data-stu-id="8207e-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="8207e-104">[IntelliSense](/visualstudio/ide/using-intellisense) 是一種可在不同整合式開發環境 (IDE)，例如 Visual Studio 中使用的程式碼完成輔助工具。</span><span class="sxs-lookup"><span data-stu-id="8207e-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="8207e-105">根據預設，在開發 .NET Core 專案時，SDK 只會包含 IntelliSense 檔案的英文版本。</span><span class="sxs-lookup"><span data-stu-id="8207e-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="8207e-106">本文說明：</span><span class="sxs-lookup"><span data-stu-id="8207e-106">This article explains:</span></span>

- <span data-ttu-id="8207e-107">如何安裝這些檔案的當地語系化版本。</span><span class="sxs-lookup"><span data-stu-id="8207e-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="8207e-108">如何修改 Visual Studio 安裝以使用不同語言。</span><span class="sxs-lookup"><span data-stu-id="8207e-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8207e-109">必要條件：</span><span class="sxs-lookup"><span data-stu-id="8207e-109">Prerequisites</span></span>

- <span data-ttu-id="8207e-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="8207e-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="8207e-111">[Visual Studio 2019 版本 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="8207e-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="8207e-112">下載及安裝當地語系化 IntelliSense 檔案</span><span class="sxs-lookup"><span data-stu-id="8207e-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8207e-113">此程序需要具備將 IntelliSense 檔案複製到 .NET Core 安裝資料夾的系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="8207e-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="8207e-114">前往[下載 IntelliSense 檔案](https://dotnet.microsoft.com/download/dotnet-core/intellisense)頁面。</span><span class="sxs-lookup"><span data-stu-id="8207e-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="8207e-115">下載要使用的 IntelliSense 語言及版本檔案。</span><span class="sxs-lookup"><span data-stu-id="8207e-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="8207e-116">解壓縮 ZIP 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="8207e-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="8207e-117">流覽至 [.NET Core Intellisense] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8207e-117">Navigate to the .NET Core Intellisense folder.</span></span>

   1. <span data-ttu-id="8207e-118">巡覽至 .NET Core 安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="8207e-118">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="8207e-119">根據預設，其位於 *%ProgramFiles%\dotnet\packs*。</span><span class="sxs-lookup"><span data-stu-id="8207e-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="8207e-120">選擇要為其安裝 IntelliSense 的 SDK，然後巡覽至相關聯的路徑。</span><span class="sxs-lookup"><span data-stu-id="8207e-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="8207e-121">下列選項可供您選擇：</span><span class="sxs-lookup"><span data-stu-id="8207e-121">You have the following options:</span></span>

      | <span data-ttu-id="8207e-122">SDK 類型</span><span class="sxs-lookup"><span data-stu-id="8207e-122">SDK type</span></span>        | <span data-ttu-id="8207e-123">{2&gt;路徑&lt;2}</span><span class="sxs-lookup"><span data-stu-id="8207e-123">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="8207e-124">.NET Core</span><span class="sxs-lookup"><span data-stu-id="8207e-124">.NET Core</span></span>       | <span data-ttu-id="8207e-125">*Microsoft.NETCore.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="8207e-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="8207e-126">Windows 桌惎</span><span class="sxs-lookup"><span data-stu-id="8207e-126">Windows Desktop</span></span> | <span data-ttu-id="8207e-127">*Microsoft.WindowsDesktop.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="8207e-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="8207e-128">.NET 標準</span><span class="sxs-lookup"><span data-stu-id="8207e-128">.NET Standard</span></span>   | <span data-ttu-id="8207e-129">*NETStandard.Library.Ref*</span><span class="sxs-lookup"><span data-stu-id="8207e-129">*NETStandard.Library.Ref*</span></span>          |
   
   1. <span data-ttu-id="8207e-130">巡覽至要為其安裝當地語系化 IntelliSense 的版本。</span><span class="sxs-lookup"><span data-stu-id="8207e-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="8207e-131">例如，*3.1.0*。</span><span class="sxs-lookup"><span data-stu-id="8207e-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="8207e-132">開啟 *ref* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8207e-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="8207e-133">開啟 Moniker 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8207e-133">Open the moniker folder.</span></span> <span data-ttu-id="8207e-134">例如，*netcoreapp3.1*。</span><span class="sxs-lookup"><span data-stu-id="8207e-134">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="8207e-135">因此，您巡覽的目標完整路徑看起來會如下：*C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*。</span><span class="sxs-lookup"><span data-stu-id="8207e-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="8207e-136">在剛開啟的 Moniker 資料夾中建立子資料夾。</span><span class="sxs-lookup"><span data-stu-id="8207e-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="8207e-137">資料夾名稱會指出所要使用的語言。</span><span class="sxs-lookup"><span data-stu-id="8207e-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="8207e-138">下表指定不同選項：</span><span class="sxs-lookup"><span data-stu-id="8207e-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="8207e-139">語言</span><span class="sxs-lookup"><span data-stu-id="8207e-139">Language</span></span>              | <span data-ttu-id="8207e-140">資料夾名稱</span><span class="sxs-lookup"><span data-stu-id="8207e-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="8207e-141">葡萄牙文(巴西)</span><span class="sxs-lookup"><span data-stu-id="8207e-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="8207e-142">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="8207e-142">*pt-br*</span></span>     |
   | <span data-ttu-id="8207e-143">中文（簡體）</span><span class="sxs-lookup"><span data-stu-id="8207e-143">Chinese (simplified)</span></span>  | <span data-ttu-id="8207e-144">*zh-hans*</span><span class="sxs-lookup"><span data-stu-id="8207e-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="8207e-145">中文（繁體）</span><span class="sxs-lookup"><span data-stu-id="8207e-145">Chinese (traditional)</span></span> | <span data-ttu-id="8207e-146">*zh-hant*</span><span class="sxs-lookup"><span data-stu-id="8207e-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="8207e-147">法文</span><span class="sxs-lookup"><span data-stu-id="8207e-147">French</span></span>                | <span data-ttu-id="8207e-148">*fr*</span><span class="sxs-lookup"><span data-stu-id="8207e-148">*fr*</span></span>        |
   | <span data-ttu-id="8207e-149">德文</span><span class="sxs-lookup"><span data-stu-id="8207e-149">German</span></span>                | <span data-ttu-id="8207e-150">*de*</span><span class="sxs-lookup"><span data-stu-id="8207e-150">*de*</span></span>        |
   | <span data-ttu-id="8207e-151">義大利文</span><span class="sxs-lookup"><span data-stu-id="8207e-151">Italian</span></span>               | <span data-ttu-id="8207e-152">*it*</span><span class="sxs-lookup"><span data-stu-id="8207e-152">*it*</span></span>        |
   | <span data-ttu-id="8207e-153">日文</span><span class="sxs-lookup"><span data-stu-id="8207e-153">Japanese</span></span>              | <span data-ttu-id="8207e-154">*ja*</span><span class="sxs-lookup"><span data-stu-id="8207e-154">*ja*</span></span>        |
   | <span data-ttu-id="8207e-155">韓文</span><span class="sxs-lookup"><span data-stu-id="8207e-155">Korean</span></span>                | <span data-ttu-id="8207e-156">*ko*</span><span class="sxs-lookup"><span data-stu-id="8207e-156">*ko*</span></span>        |
   | <span data-ttu-id="8207e-157">俄文</span><span class="sxs-lookup"><span data-stu-id="8207e-157">Russian</span></span>               | <span data-ttu-id="8207e-158">*ru*</span><span class="sxs-lookup"><span data-stu-id="8207e-158">*ru*</span></span>        |
   | <span data-ttu-id="8207e-159">西班牙文</span><span class="sxs-lookup"><span data-stu-id="8207e-159">Spanish</span></span>               | <span data-ttu-id="8207e-160">*es*</span><span class="sxs-lookup"><span data-stu-id="8207e-160">*es*</span></span>        |

1. <span data-ttu-id="8207e-161">將您在步驟 3 解壓縮的 *.xml* 檔案複製到此新資料夾。</span><span class="sxs-lookup"><span data-stu-id="8207e-161">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="8207e-162">*.xml* 檔案會依照 SDK 資料夾細分，因此請將這些檔案複製到在步驟 4 選擇的相符 SDK。</span><span class="sxs-lookup"><span data-stu-id="8207e-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="8207e-163">修改 Visual Studio 語言</span><span class="sxs-lookup"><span data-stu-id="8207e-163">Modify Visual Studio language</span></span>

<span data-ttu-id="8207e-164">若要讓 Visual Studio 使用不同的 IntelliSense 語言，請安裝適當的語言套件。</span><span class="sxs-lookup"><span data-stu-id="8207e-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="8207e-165">這可以透過在[安裝期間](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional)或於稍後修改 Visual Studio 安裝來進行。</span><span class="sxs-lookup"><span data-stu-id="8207e-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="8207e-166">如果您已將 Visual Studio 設為選擇的語言，則 IntelliSense 安裝便已準備就緒。</span><span class="sxs-lookup"><span data-stu-id="8207e-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="8207e-167">安裝語言套件</span><span class="sxs-lookup"><span data-stu-id="8207e-167">Install the language pack</span></span>

<span data-ttu-id="8207e-168">如果您並未在安裝期間安裝所需要的語言套件，請遵循以下方式更新 Visual Studio 來安裝語言套件：</span><span class="sxs-lookup"><span data-stu-id="8207e-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8207e-169">若要安裝、更新或修改 Visual Studio，您必須使用具有系統管理員許可權的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="8207e-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="8207e-170">如需詳細資訊，請參閱[使用者權限和 Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="8207e-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="8207e-171">在電腦上找到 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="8207e-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="8207e-172">例如，在執行 Windows 10，的電腦上，選取 [開始]，然後捲動到字母 [V]，它在其中列為 [Visual Studio Installer]。</span><span class="sxs-lookup"><span data-stu-id="8207e-172">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![在 Windows 上開啟 Visual Studio 安裝程式](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="8207e-174">您也可以在下列位置找到 Visual Studio 安裝程式：</span><span class="sxs-lookup"><span data-stu-id="8207e-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="8207e-175">您可能需要更新安裝程式才能繼續。</span><span class="sxs-lookup"><span data-stu-id="8207e-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="8207e-176">若是如此，請遵循提示。</span><span class="sxs-lookup"><span data-stu-id="8207e-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="8207e-177">在安裝程式中，尋找要新增語言套件的目標 Visual Studio 版本，然後選擇 [修改]。</span><span class="sxs-lookup"><span data-stu-id="8207e-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![更新或修改 Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="8207e-179">如果您沒有看到 [修改] 按鈕，但有看到 [更新] 按鈕，則表示您需要先更新 Visual Studio，之後才能修改安裝。</span><span class="sxs-lookup"><span data-stu-id="8207e-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="8207e-180">更新完成後，[修改] 按鈕應該會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8207e-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="8207e-181">在 [語言套件] 索引標籤中，選取或取消選取要安裝或解除安裝的語言。</span><span class="sxs-lookup"><span data-stu-id="8207e-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Visual Studio [語言套件] 索引標籤](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="8207e-183">選擇 [修改]。</span><span class="sxs-lookup"><span data-stu-id="8207e-183">Choose **Modify**.</span></span> <span data-ttu-id="8207e-184">更新便會開始。</span><span class="sxs-lookup"><span data-stu-id="8207e-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="8207e-185">修改 Visual Studio 中的語言設定</span><span class="sxs-lookup"><span data-stu-id="8207e-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="8207e-186">在安裝所需要的語言套件後，請修改您的 Visual Studio 設定，以使用不同語言：</span><span class="sxs-lookup"><span data-stu-id="8207e-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="8207e-187">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8207e-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="8207e-188">在 [開始] 視窗中，選擇 [不使用程式碼繼續]。</span><span class="sxs-lookup"><span data-stu-id="8207e-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="8207e-189">在功能表列上，選取 [**工具**] [ > **選項**]。</span><span class="sxs-lookup"><span data-stu-id="8207e-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="8207e-190">[選項] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="8207e-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="8207e-191">在 [**環境**] 節點底下，選擇 [**國際設定**]。</span><span class="sxs-lookup"><span data-stu-id="8207e-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="8207e-192">在 [語言] 下拉式清單中，選取所需要的語言。</span><span class="sxs-lookup"><span data-stu-id="8207e-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="8207e-193">選擇 [ **確定**]。</span><span class="sxs-lookup"><span data-stu-id="8207e-193">Choose **OK**.</span></span> 

1. <span data-ttu-id="8207e-194">對話方塊會通知您必須重新啟動 Visual Studio，才能使變更生效。</span><span class="sxs-lookup"><span data-stu-id="8207e-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="8207e-195">選擇 [ **確定**]。</span><span class="sxs-lookup"><span data-stu-id="8207e-195">Choose **OK**.</span></span>

1. <span data-ttu-id="8207e-196">重新啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8207e-196">Restart Visual Studio.</span></span>

<span data-ttu-id="8207e-197">之後在開啟以您剛安裝 IntelliSense 檔案版本為目標的 .NET Core 專案時，IntelliSense 應該就會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="8207e-197">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="8207e-198">請參閱</span><span class="sxs-lookup"><span data-stu-id="8207e-198">See also</span></span>

- [<span data-ttu-id="8207e-199">Visual Studio 中的 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="8207e-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
