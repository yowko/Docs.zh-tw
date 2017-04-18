---
title: ".NET 的核心和開放原始碼 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 6
---
# .NET 的核心和開放原始碼
.NET Core 是 .NET Framework 的模組化版本，設計目的在能夠移植到不同的平台，以最大化程式碼重複使用及共用的可能性。 此外，.NET Core 將會以開放原始碼提供，並接受社群的參與。 本主題將回答一些有關 .NET Core 及如何存取及提供和開放原始碼套件的常見問題。  
  
<a name="BKMK_WhatisNETCore"></a>   
## 什麼是 .NET Core？  
 如前所述，.NET Core 是 .NET Framework 的模組化版本，設計目的在能夠移植到不同的平台。  
  
 .NET Core 雖然只有完整版 .NET Framework 的部分功能，但因為其主要功能可以實作您所需要的應用程式功能，並不分平台地重複使用此程式碼，所以可以移植到不同平台上。 在過去，不同平台之不同版本的 .NET 在關鍵作業上缺乏共通的功能，例如讀取本機檔案。 .NET Core 支援的 Microsoft 平台對象包括傳統桌上型電腦的 Windows，以及 Windows 裝置與 Windows Phone。 在使用第三方工具 \(例如 Xamarin\) 時，.NET Core 也能移植到 IOS 及 Android 裝置。 除此之外，.NET Core 很快也能在 Mac 及 Linux 作業系統上使用，讓 Web 應用程式也可在這些系統上執行。  
  
 .NET Core 因為是透過 NuGet 以較小型的組件套件發行，所以稱為模組化版本。 不同於大型組件會包含大部分的核心功能，.NET Core 著眼於特定功能，會以較小型的套件提供。 不僅開發模型變得更為靈活，您更能針對應用程式與程式庫的需要，挑選您所需要的功能部分。 如需由 NuGet 發行之 .NET 套件的詳細資訊，請參閱 [.NET Framework 和 Out\-of\-Band 發行版本](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)。  
  
 下列是一些有關 .NET Core 的常見問題。  
  
### 如何才能發揮 .NET Core 的最大功能？  
 對於現有的應用程式，使用可攜式類別程式庫 \(PCL\)、通用應用程式專案，並區分商務邏輯與平台特有的程式碼，是最能發揮 .NET Core 及最大化程式碼重複使用能力的最佳方式。 對於應用程式，「模型\-檢視\-控制器」\(MVC\) 或「模型檢視\-檢視模型」\(MVVM\) 這兩種模式都是很好的選擇，可以讓應用程式很容易就能移轉到.NET Core。  
  
### .NET Core 對於相容性及部署有什麼影響？  
 在部署情節上或有差異，但部署本身仍是十分容易。 .NET Framework 將隨附於 Windows 散發，而更新方式與現今無異，仍會透過 Microsoft Update。 在某些情況下，您的應用程式需要仰賴 .NET Framework 部署到磁碟上，而在其他情況下，您的應用程式卻又需要仰賴隨應用程式套件一起部署的 .NET 組件。 此外，版本間的相容性對 .NET Framework 而言仍是極為重要，因此，若您應用程式執行所用的組件版本，較編輯時所用的組件版本新，其行為將不會有任何改變。  
  
|情節|部署|  
|--------|--------|  
|在 Windows 電腦上執行的 Windows 桌面應用程式及 ASP.NET 應用程式|部署方式與現今無異。 需要仰賴伺服器或使用者電腦上所安裝之 .NET framework 的應用程式。 若未安裝 .NET Framework，將會提示使用者加以安裝。 使用者也可鏈結 .NET 安裝與應用程式。 當您使用 .NET Framework 所未含括的 .NET Core 組件時，這些組件會隨附在應用程式套件中。 此外，若同一個應用程式參考了不同版本的同一組件，該應用程式將被重新導向至較新的組件。 如需詳細資訊，請參閱 [將應用程式層級的組件版本重新導向](../../../docs/framework/configure-apps/redirect-assembly-versions.md#BKMK_Redirectingassemblyversionsattheapplevel) 和 [如何：啟用和停用自動繫結重新導向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)。<br /><br /> 如需 .NET 部署的詳細資訊，請參閱 [開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)。|  
|經由 Windows 及 Windows Phone 市集發行的 Windows 及 Windows Phone 應用程式|部署方式與現今相同，且應用程式會使用作業系統隨附的 .NET Framework 組件。 若應用程式使用不屬於 .NET Framework 之 .NET Core 組件中所發行的功能，該組件將會隨附在應用程式套件中。 若同一應用程式參考多種版本的同一組件，這些應用程式會自動使用較新版的組件。|  
|ASP.NET Core 5.0 應用程式|.NET Core 組件必須跟隨著應用程式，亦即組件必須隨著應用程式套件一起部署。 如需 ASP.NET Core 5.0 的詳細資訊，請參閱 [ASP.NET 5 概觀](http://www.asp.net/vnext/overview/aspnet-vnext/aspnet-5-overview)。|  
|利用 Xamarin 工具建置在其他平台上執行的應用程式|這些應用程式目前會隨著應用程式套件隨附的精簡 Mono 組件集一起部署。 隨著更多 .NET Core 組件轉為開放原始碼，此方式可能也會有所變更。|  
  
<a name="BKMK_NETCoreOpenSourcePackages"></a>   
## .NET Core 開放原始碼套件  
 除了模組化的 .NET Framework 之外，Microsoft 也在 [MIT](https://github.com/dotnet/corefx/blob/master/LICENSE) 授權之下，將 .NET Core 套件以開放原始碼方式於 [GitHub](https://github.com/) 上提供。 這表示您可以像您對您在 GitHub 上找到的其他開放原始碼套件一樣，複製 Git 儲存機制、讀取及編譯程式碼，並提交提取要求。 由於我們對於品質及相容性的堅持，每一個提取要求都會先經過仔細評估後才予接受。 下列是一些常見問題。  
  
### 如何取得及建置程式碼？  
 .NET Core 的原始檔套件都會存放在 `GitHub` 上，而 GitHub 會使用 `Git` 做為原始檔控制系統。 若要存取及建置程式碼，您對於 [Git](http://git-scm.com/)、[GitHub](https://github.com/dotnet/corefx) 及 [Visual Studio](http://msdn.microsoft.com/vstudio/aa718325.aspx) 應該具備一些基本的認識，但下列步驟提供一些資訊及連結，可以協助您開始使用。  
  
 若要設定 Git 及 GitHub，請參閱 GitHub 網站上的[設定 Git](https://help.github.com/articles/set-up-git/)。  
  
 若要存取.NET Framework 程式碼，您必須分叉包含此程式碼的 Git 儲存機制，並將其複製到您的開發電腦上。 若要分岔程式碼，請瀏覽至儲存機制，然後按一下瀏覽器右上角的 \[分岔\]。 您可以使用 GitHub 應用程式，或在 GitHub 命令介面中的命令列上複製分叉。 若要在 GitHub 命令介面中複製儲存機制，請執行下列命令：  
  
```  
git clone https://github.com/dotnet/corefx  
```  
  
 若要建置程式碼，應先安裝 Visual Studio 2013。 您可以使用 Visual Studio 201 開啟及建置解決方案，然後按 F5，也可以使用開發人員命令提示字元在命令列上進行建置。 若要使用命令提示字元建置，請開啟開發人員命令提示字元，然後瀏覽至您用於複製原始碼的資料夾。 接著輸入：  
  
```  
build.cmd  
  
```  
  
 如需如何存取開發人員命令提示字元的詳細資訊，請參閱 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
### 提交程式碼的準則有哪些？  
 在我們可以將您的工作合併到主要分支之前，您必須先簽署[參與者授權合約 \(CLA\)](https://cla.dotnetfoundation.org/)。  
  
 我們接受使用分叉及提取模型之社群的參與。 您應分叉及複製程式碼，並將提取要求提交到.NET Framework 的主要分支。 如需提取要求的詳細資訊，請參閱[使用提取要求](https://help.github.com/articles/using-pull-requests/)。 如需提交提取要求之準則的詳細資訊，請參閱 [.NET Core 參與指南](https://github.com/dotnet/corefx/wiki/Contributing)。  
  
### 為什麼不接受我的提取要求？  
 當我們拒絕您的要求時，我們會提供原因，但通常都是因為 Microsoft 對於程式碼品質與相容性的強力堅持所致。 您的提取要求若不被接受，可能是未遵守我們的程式碼撰寫準則、提交的程式碼未經適當的測試，或有 API 不相容的問題。 此外，您的程式碼變更也應符合 .NET Framework 的藍圖規劃。 如需程式碼撰寫方針和詳細資訊，請參閱 [.NET Core 參與指南](https://github.com/dotnet/corefx/wiki/Contributing)。  
  
## 請參閱  
 [.NET 是開啟原始碼](http://blogs.msdn.com/b/dotnet/archive/2014/11/12/net-core-is-open-source.aspx)   
 [.NET 開放原始碼 Curah](https://curah.microsoft.com/254870/net-core-open-source)   
 [ASP.NET 5 概觀](http://www.asp.net/vnext/overview/aspnet-vnext/aspnet-5-overview)