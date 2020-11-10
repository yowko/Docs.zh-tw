---
title: 安裝當地語系化的 IntelliSense 檔案
description: 瞭解如何設定您的開發電腦，以針對 .NET 5 + 專案使用當地語系化的 IntelliSense 檔案 (包括 Visual Studio 中的 .NET Core) 。
ms.date: 11/06/2020
ms.openlocfilehash: 121439199f0de6d29a18ea55031976680fc1f833
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439816"
---
# <a name="how-to-install-localized-intellisense-files-for-net"></a><span data-ttu-id="4a181-103">如何安裝適用于 .NET 的當地語系化 IntelliSense 檔案</span><span class="sxs-lookup"><span data-stu-id="4a181-103">How to install localized IntelliSense files for .NET</span></span>

<span data-ttu-id="4a181-104">[IntelliSense](/visualstudio/ide/using-intellisense) 是一種程式碼完成的輔助工具，可用於不同的整合式開發環境 (ide) ，例如 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4a181-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that's available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="4a181-105">根據預設，當您開發 .NET 專案時，SDK 只會包含英文版的 IntelliSense 檔案。</span><span class="sxs-lookup"><span data-stu-id="4a181-105">By default, when you're developing .NET projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="4a181-106">本文說明：</span><span class="sxs-lookup"><span data-stu-id="4a181-106">This article explains:</span></span>

- <span data-ttu-id="4a181-107">如何安裝這些檔案的當地語系化版本。</span><span class="sxs-lookup"><span data-stu-id="4a181-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="4a181-108">如何修改 Visual Studio 安裝以使用不同語言。</span><span class="sxs-lookup"><span data-stu-id="4a181-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4a181-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="4a181-109">Prerequisites</span></span>

- <span data-ttu-id="4a181-110">[.Net Core 3.0 sdk](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本（例如 [.net 5 sdk](https://dotnet.microsoft.com/download/dotnet/5.0)）。</span><span class="sxs-lookup"><span data-stu-id="4a181-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version, such as [.NET 5 SDK](https://dotnet.microsoft.com/download/dotnet/5.0).</span></span>
- <span data-ttu-id="4a181-111">[Visual Studio 2019 版本 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="4a181-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="4a181-112">下載及安裝當地語系化 IntelliSense 檔案</span><span class="sxs-lookup"><span data-stu-id="4a181-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a181-113">此程式會要求您必須擁有系統管理員許可權，才能將 IntelliSense 檔案複製到 .NET 安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a181-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET installation folder.</span></span>

1. <span data-ttu-id="4a181-114">前往[下載 IntelliSense 檔案](https://dotnet.microsoft.com/download/intellisense)頁面。</span><span class="sxs-lookup"><span data-stu-id="4a181-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/intellisense) page.</span></span>

1. <span data-ttu-id="4a181-115">下載要使用的 IntelliSense 語言及版本檔案。</span><span class="sxs-lookup"><span data-stu-id="4a181-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="4a181-116">解壓縮 ZIP 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="4a181-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="4a181-117">流覽至 [.NET Intellisense] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a181-117">Navigate to the .NET Intellisense folder.</span></span>

   1. <span data-ttu-id="4a181-118">流覽至 .NET 安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a181-118">Navigate to the .NET installation folder.</span></span> <span data-ttu-id="4a181-119">根據預設，其位於 *%ProgramFiles%\dotnet\packs* 。</span><span class="sxs-lookup"><span data-stu-id="4a181-119">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>
   1. <span data-ttu-id="4a181-120">選擇要為其安裝 IntelliSense 的 SDK，然後巡覽至相關聯的路徑。</span><span class="sxs-lookup"><span data-stu-id="4a181-120">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="4a181-121">下列選項可供您選擇：</span><span class="sxs-lookup"><span data-stu-id="4a181-121">You have the following options:</span></span>

      | <span data-ttu-id="4a181-122">SDK 類型</span><span class="sxs-lookup"><span data-stu-id="4a181-122">SDK type</span></span>              | <span data-ttu-id="4a181-123">路徑</span><span class="sxs-lookup"><span data-stu-id="4a181-123">Path</span></span>                               |
      |-----------------------|------------------------------------|
      | <span data-ttu-id="4a181-124">.NET 5 + 和 .NET Core</span><span class="sxs-lookup"><span data-stu-id="4a181-124">.NET 5+ and .NET Core</span></span> | <span data-ttu-id="4a181-125">*Microsoft.NETCore.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="4a181-125">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="4a181-126">Windows 桌面</span><span class="sxs-lookup"><span data-stu-id="4a181-126">Windows Desktop</span></span>       | <span data-ttu-id="4a181-127">*Microsoft.WindowsDesktop.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="4a181-127">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="4a181-128">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="4a181-128">.NET Standard</span></span>         | <span data-ttu-id="4a181-129">*NETStandard.Library.Ref*</span><span class="sxs-lookup"><span data-stu-id="4a181-129">*NETStandard.Library.Ref*</span></span>          |

   1. <span data-ttu-id="4a181-130">巡覽至要為其安裝當地語系化 IntelliSense 的版本。</span><span class="sxs-lookup"><span data-stu-id="4a181-130">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="4a181-131">例如， *3.1.0* 。</span><span class="sxs-lookup"><span data-stu-id="4a181-131">For example, *3.1.0*.</span></span>
   1. <span data-ttu-id="4a181-132">開啟 *ref* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a181-132">Open the *ref* folder.</span></span>
   1. <span data-ttu-id="4a181-133">開啟 Moniker 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a181-133">Open the moniker folder.</span></span> <span data-ttu-id="4a181-134">例如， *net 5.0* 。</span><span class="sxs-lookup"><span data-stu-id="4a181-134">For example, *net5.0*.</span></span>

   <span data-ttu-id="4a181-135">因此，您流覽的完整路徑看起來會像 *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\5.0.0\ref\net5.0* 。</span><span class="sxs-lookup"><span data-stu-id="4a181-135">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\5.0.0\ref\net5.0*.</span></span>

1. <span data-ttu-id="4a181-136">在剛開啟的 Moniker 資料夾中建立子資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a181-136">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="4a181-137">資料夾名稱會指出所要使用的語言。</span><span class="sxs-lookup"><span data-stu-id="4a181-137">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="4a181-138">下表指定不同選項：</span><span class="sxs-lookup"><span data-stu-id="4a181-138">The following table specifies the different options:</span></span>

   | <span data-ttu-id="4a181-139">語言</span><span class="sxs-lookup"><span data-stu-id="4a181-139">Language</span></span>              | <span data-ttu-id="4a181-140">資料夾名稱</span><span class="sxs-lookup"><span data-stu-id="4a181-140">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="4a181-141">巴西葡萄牙文</span><span class="sxs-lookup"><span data-stu-id="4a181-141">Brazilian Portuguese</span></span>  | <span data-ttu-id="4a181-142">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="4a181-142">*pt-br*</span></span>     |
   | <span data-ttu-id="4a181-143">中文 (簡體)</span><span class="sxs-lookup"><span data-stu-id="4a181-143">Chinese (simplified)</span></span>  | <span data-ttu-id="4a181-144">*zh-hans*</span><span class="sxs-lookup"><span data-stu-id="4a181-144">*zh-hans*</span></span>   |
   | <span data-ttu-id="4a181-145">中文 (繁體)</span><span class="sxs-lookup"><span data-stu-id="4a181-145">Chinese (traditional)</span></span> | <span data-ttu-id="4a181-146">*zh-zh-hant*</span><span class="sxs-lookup"><span data-stu-id="4a181-146">*zh-hant*</span></span>   |
   | <span data-ttu-id="4a181-147">法文</span><span class="sxs-lookup"><span data-stu-id="4a181-147">French</span></span>                | <span data-ttu-id="4a181-148">*fr*</span><span class="sxs-lookup"><span data-stu-id="4a181-148">*fr*</span></span>        |
   | <span data-ttu-id="4a181-149">德文</span><span class="sxs-lookup"><span data-stu-id="4a181-149">German</span></span>                | <span data-ttu-id="4a181-150">*de*</span><span class="sxs-lookup"><span data-stu-id="4a181-150">*de*</span></span>        |
   | <span data-ttu-id="4a181-151">義大利文</span><span class="sxs-lookup"><span data-stu-id="4a181-151">Italian</span></span>               | <span data-ttu-id="4a181-152">*it*</span><span class="sxs-lookup"><span data-stu-id="4a181-152">*it*</span></span>        |
   | <span data-ttu-id="4a181-153">日文</span><span class="sxs-lookup"><span data-stu-id="4a181-153">Japanese</span></span>              | <span data-ttu-id="4a181-154">*ja*</span><span class="sxs-lookup"><span data-stu-id="4a181-154">*ja*</span></span>        |
   | <span data-ttu-id="4a181-155">韓文</span><span class="sxs-lookup"><span data-stu-id="4a181-155">Korean</span></span>                | <span data-ttu-id="4a181-156">*ko*</span><span class="sxs-lookup"><span data-stu-id="4a181-156">*ko*</span></span>        |
   | <span data-ttu-id="4a181-157">俄文</span><span class="sxs-lookup"><span data-stu-id="4a181-157">Russian</span></span>               | <span data-ttu-id="4a181-158">*ru*</span><span class="sxs-lookup"><span data-stu-id="4a181-158">*ru*</span></span>        |
   | <span data-ttu-id="4a181-159">西班牙文</span><span class="sxs-lookup"><span data-stu-id="4a181-159">Spanish</span></span>               | <span data-ttu-id="4a181-160">*es*</span><span class="sxs-lookup"><span data-stu-id="4a181-160">*es*</span></span>        |

1. <span data-ttu-id="4a181-161">將您在步驟3中解壓縮的 *.xml* 檔案複製到這個新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a181-161">Copy the *.xml* files you extracted in step 3 to this new folder.</span></span> <span data-ttu-id="4a181-162">*.Xml* 檔案會依 SDK 資料夾細分，因此請將它們複製到您在步驟4中選擇的相符 SDK。</span><span class="sxs-lookup"><span data-stu-id="4a181-162">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose in step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="4a181-163">修改 Visual Studio 語言</span><span class="sxs-lookup"><span data-stu-id="4a181-163">Modify Visual Studio language</span></span>

<span data-ttu-id="4a181-164">若要讓 Visual Studio 使用不同的 IntelliSense 語言，請安裝適當的語言套件。</span><span class="sxs-lookup"><span data-stu-id="4a181-164">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="4a181-165">這可以透過在[安裝期間](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional)或於稍後修改 Visual Studio 安裝來進行。</span><span class="sxs-lookup"><span data-stu-id="4a181-165">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="4a181-166">如果您已將 Visual Studio 設為選擇的語言，則 IntelliSense 安裝便已準備就緒。</span><span class="sxs-lookup"><span data-stu-id="4a181-166">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="4a181-167">安裝語言套件</span><span class="sxs-lookup"><span data-stu-id="4a181-167">Install the language pack</span></span>

<span data-ttu-id="4a181-168">如果您並未在安裝期間安裝所需要的語言套件，請遵循以下方式更新 Visual Studio 來安裝語言套件：</span><span class="sxs-lookup"><span data-stu-id="4a181-168">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a181-169">若要安裝、更新或修改 Visual Studio，您必須使用具有系統管理員許可權的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="4a181-169">To install, update, or modify Visual Studio, you must log on with an account that has administrator permission.</span></span> <span data-ttu-id="4a181-170">如需詳細資訊，請參閱 [使用者權限和 Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="4a181-170">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="4a181-171">在電腦上找到 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="4a181-171">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="4a181-172">例如，在執行 Windows 10，的電腦上，選取 [開始]，然後捲動到字母 [V]，它在其中列為 [Visual Studio Installer]。</span><span class="sxs-lookup"><span data-stu-id="4a181-172">For example, on a computer running Windows 10, select **Start** , and then scroll to the letter **V** , where it's listed as **Visual Studio Installer**.</span></span>

   ![在 Windows 上開啟 Visual Studio 安裝程式](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="4a181-174">您也可以在下列位置找到 Visual Studio 安裝程式：</span><span class="sxs-lookup"><span data-stu-id="4a181-174">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="4a181-175">您可能需要更新安裝程式才能繼續。</span><span class="sxs-lookup"><span data-stu-id="4a181-175">You might have to update the installer before continuing.</span></span> <span data-ttu-id="4a181-176">若是如此，請遵循提示。</span><span class="sxs-lookup"><span data-stu-id="4a181-176">If so, follow the prompts.</span></span>

1. <span data-ttu-id="4a181-177">在安裝程式中，尋找要新增語言套件的目標 Visual Studio 版本，然後選擇 [修改]。</span><span class="sxs-lookup"><span data-stu-id="4a181-177">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![更新或修改 Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="4a181-179">如果您沒有看到 [修改] 按鈕，但有看到 [更新] 按鈕，則表示您需要先更新 Visual Studio，之後才能修改安裝。</span><span class="sxs-lookup"><span data-stu-id="4a181-179">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="4a181-180">更新完成後，[修改] 按鈕應該會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4a181-180">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="4a181-181">在 [語言套件] 索引標籤中，選取或取消選取要安裝或解除安裝的語言。</span><span class="sxs-lookup"><span data-stu-id="4a181-181">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Visual Studio [語言套件] 索引標籤](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="4a181-183">選擇 [修改]。</span><span class="sxs-lookup"><span data-stu-id="4a181-183">Choose **Modify**.</span></span> <span data-ttu-id="4a181-184">更新會開始進行。</span><span class="sxs-lookup"><span data-stu-id="4a181-184">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="4a181-185">修改 Visual Studio 中的語言設定</span><span class="sxs-lookup"><span data-stu-id="4a181-185">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="4a181-186">在安裝所需要的語言套件後，請修改您的 Visual Studio 設定，以使用不同語言：</span><span class="sxs-lookup"><span data-stu-id="4a181-186">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="4a181-187">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4a181-187">Open Visual Studio.</span></span>

1. <span data-ttu-id="4a181-188">在 [開始] 視窗中，選擇 [不使用程式碼繼續]。</span><span class="sxs-lookup"><span data-stu-id="4a181-188">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="4a181-189">在功能表列上選取 [工具] > [選項]。</span><span class="sxs-lookup"><span data-stu-id="4a181-189">On the menu bar, select **Tools** > **Options**.</span></span> <span data-ttu-id="4a181-190">[選項] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="4a181-190">The Options dialog opens.</span></span>

1. <span data-ttu-id="4a181-191">在 [ **環境** ] 節點下，選擇 [ **國際設定** ]。</span><span class="sxs-lookup"><span data-stu-id="4a181-191">Under the **Environment** node, choose **International Settings**.</span></span>

1. <span data-ttu-id="4a181-192">在 [語言] 下拉式清單中，選取所需要的語言。</span><span class="sxs-lookup"><span data-stu-id="4a181-192">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="4a181-193">選擇 [確定]。</span><span class="sxs-lookup"><span data-stu-id="4a181-193">Choose **OK**.</span></span>

1. <span data-ttu-id="4a181-194">對話方塊會通知您必須重新啟動 Visual Studio，才能使變更生效。</span><span class="sxs-lookup"><span data-stu-id="4a181-194">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="4a181-195">選擇 [確定]。</span><span class="sxs-lookup"><span data-stu-id="4a181-195">Choose **OK**.</span></span>

1. <span data-ttu-id="4a181-196">重新啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4a181-196">Restart Visual Studio.</span></span>

<span data-ttu-id="4a181-197">之後，當您開啟以您剛剛安裝的 IntelliSense 檔案版本為目標的 .NET 專案時，IntelliSense 應該會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="4a181-197">After this, your IntelliSense should work as expected when you open a .NET project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a181-198">請參閱</span><span class="sxs-lookup"><span data-stu-id="4a181-198">See also</span></span>

- [<span data-ttu-id="4a181-199">Visual Studio 中的 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="4a181-199">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
