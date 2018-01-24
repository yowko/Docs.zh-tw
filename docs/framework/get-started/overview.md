---
title: ".NET Framework 的概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
caps.latest.revision: "34"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffe4670ef07b0a9b541bf2099958aa943bba2f68
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="overview-of-the-net-framework"></a>.NET Framework 的概觀

.NET Framework 是支援建置和執行新一代應用程式及 XML Web Service 的技術。 .NET Framework 是專為實現以下目標所設計的：

- 提供一致的物件導向程式設計環境，不論目的碼 (Object Code) 是在本機中儲存及執行、在本機執行但分散至網際網路或在遠端執行。

- 提供可減少軟體部署和版本控制衝突的程式碼執行環境。

- 提供加強程式碼安全執行的程式碼執行環境，包括未知或非完全信任之協力廠商所建立的程式碼。

- 提供可消除編寫指令碼或解譯環境效能問題的程式碼執行環境。

- 使開發人員在開發各類應用程式 (例如 Windows 架構應用程式和 Web 架構應用程式) 時享有一致的體驗。

- 根據業界標準建構所有通訊，確保以 .NET Framework 為基礎的程式碼能與任何其他程式碼整合。

> [!NOTE]
> 如需適用於使用者和開發人員的 .NET Framework 一般簡介，請參閱[使用者入門](../../../docs/framework/get-started/index.md)。

.NET Framework 是由 Common Language Runtime (CLR) 和 .NET Framework 類別庫所組成。 Common Language Runtime 是 .NET Framework 的基礎。 請將執行階段視為在執行階段管理程式碼的代理程式，可提供記憶體管理、執行緒管理和遠端作業等核心服務，並同時強制執行嚴格的型別安全及其他形式的程式碼精確度，以提升安全性和穩定性。 事實上，程式碼管理的概念是此執行階段的基本原則。 針對執行階段所開發的程式碼稱為 Managed 程式碼，而不針對執行階段所開發的程式碼稱為 Unmanaged 程式碼。 類別庫是範圍廣泛、物件導向、可重複使用類型的集合，您可用它來開發應用程式，範圍從傳統命令列或圖形使用者介面 (GUI) 應用程式到以 ASP.NET 所提供最新創新方式為基礎的應用程式，例如 Web Form 和 XML Web Service，都包括在內。

.NET Framework 可由 Unmanaged 元件裝載，此類元件會將 Common Language Runtime 載入其處理序並初始化 Managed 程式碼的執行，因此建立出能同時運用 Managed 和 Unmanaged 功能的軟體環境。 .NET Framework 不只提供數個執行階段主機，也支援協力廠商執行階段主機的開發。

例如，ASP.NET 裝載執行階段以提供可擴充、伺服器端的 Managed 程式碼環境。 ASP.NET 可直接搭配執行階段作業，以啟用 ASP.NET 應用程式和 XML Web Service，本主題稍後將討論這兩者。

Internet Explorer 是裝載執行階段的 Unmanaged 應用程式範例 (採用 MIME 類型擴充的形式)。 使用 Internet Explorer 裝載執行階段，讓您能夠將 Managed 元件或 Windows Form 控制項嵌入 HTML 文件。 以這種方式裝載執行階段，就會讓 Managed 行動程式碼變得可行，不過只有 Managed 程式碼才能提供明顯的改善，例如非完全信任執行和隔離檔案儲存。

下圖顯示 Common Language Runtime 和類別庫與您的應用程式及整體系統的關係。 下圖也顯示 Managed 程式碼是如何在較大架構中運作的。

![較大型架構中的 Managed 程式碼](../../../docs/framework/get-started/media/circle.gif "圓形").NET Framework 關係架構圖

下列章節將更詳細說明 .NET Framework 的主要功能。

## <a name="features-of-the-common-language-runtime"></a>Common Language Runtime 的功能

Common Language Runtime 負責管理記憶體、執行緒執行、程式碼執行、程式碼安全驗證、編譯 (Compilation) 和其他系統服務。 這些功能都內建到在 Common Language Runtime 上執行的 Managed 程式碼中。

就安全性而言，Managed 元件會根據若干因素而被授予不同程度的信任，這些因素包括元件的原始出處 (例如網際網路、企業網路或本機電腦)。 這表示即使是在相同作用中的應用程式中使用，Managed 元件可能可以也可能無法執行檔案存取作業、註冊存取作業或其他易受影響的功能。

Runtime 也會藉由實作嚴格的型別和程式碼驗證基礎架構，也就是一般型別系統 (CTS)，強制執行程式碼的加強性。 CTS 確保所有 Managed 程式碼都能夠自我描述。 不同的 Microsoft 和協力廠商語言編譯器會產生符合 CTS 的 Managed 程式碼。 這表示 Managed 程式碼不但能夠使用其他 Managed 型別和執行個體，同時還能嚴格強制執行型別精確度和型別安全。

此外，Runtime 的 Managed 環境排除許多常見的軟體問題。 例如，Runtime 能夠自動處理物件配置，並管理對物件的參考，而且在不再用它們時加以釋放。 這種自動記憶體管理解決了兩個最常見的應用程式錯誤：記憶體流失和無效的記憶體參考。

Runtime 也提升開發人員的產能。 例如，程式設計人員可以用自己選擇的開發語言撰寫應用程式，但仍充分利用其他開發人員以其他語言所撰寫的執行階段、類別庫和元件。 選擇以執行階段為目標來開發編譯器的廠商都可作到這一點。 以 .NET Framework 為目標的語言編譯器可以將 .NET Framework 的功能提供給以該語言所撰寫的現有程式碼使用，大幅簡化現有應用程式的移轉程序。

Runtime 是為未來軟體所設計的，但它也支援目前和過去的軟體。 Managed 和 Unmanaged 程式碼的互通性 (Interoperability)，讓開發人員繼續使用必要的 COM 元件和 DLL。

Runtime 是為增強效能所設計的。 雖然 Common Language Runtime 提供許多標準的執行階段服務，但未曾解譯 Managed 程式碼。 透過一項稱為 Just-In-Time (JIT) 編譯的功能，所有的 Managed 程式碼都可使用執行所在系統的原生機器語言執行。 同時，記憶體管理員移除分散的記憶體的可能性，增加記憶體參考位置，以進一步提高效能。

最後，執行階段可由高效能的伺服器端應用程式裝載，例如 Microsoft SQL Server 和 Internet Information Services (IIS)。 這個基礎架構讓您使用 Managed 程式碼撰寫商務邏輯的同時，仍能夠享受到由業界最佳、可支援執行階段主應用程式的企業伺服器所提供的超高效能。

## <a name="net-framework-class-library"></a>.NET Framework 類別庫

.NET Framework 類別庫是與 Common Language Runtime 緊密整合的可重複使用型別的集合。 此類別庫為物件導向，能提供類型讓您撰寫自己的 Managed 程式碼從其衍生功能。 這不但使 .NET Framework 類型易於使用，也減少了學習 .NET Framework 新功能所需的時間。 此外，協力廠商元件也可以與 .NET Framework 中的類別完美整合。

例如，.NET Framework 集合類別會實作一組介面，以開發您自己的集合類別。 您的集合類別會與 .NET Framework 中的類別完美結合。

如同您對物件導向類別庫的期望，.NET Framework 型別讓您完成許多常見的程式設計工作，包括字串管理、資料收集、資料庫連接和檔案存取等。 除了通用工作，類別庫還包括能夠支援各種特定開發案例的型別。 您可以使用 .NET Framework 開發下列類型的應用程式和服務：

- 主控台應用程式。 請參閱[建置主控台應用程式](../../../docs/standard/building-console-apps.md)。

- Windows GUI 應用程式 (Windows Forms)。 請參閱 [Windows Forms](../../../docs/framework/winforms/index.md)。

- Windows Presentation Foundation (WPF) 應用程式。 請參閱 [Windows Presentation Foundation](../../../docs/framework/wpf/index.md)。

- ASP.NET 應用程式。 請參閱[使用 ASP.NET 的 Web 應用程式](../../../docs/framework/develop-web-apps-with-aspnet.md)。

- Windows 服務 請參閱 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)。

- 使用 Windows Communication Foundation (WCF) 的服務導向應用程式。 請參閱[使用 WCF 以服務為導向的應用程式](../../../docs/framework/wcf/index.md)。

- 使用 Windows Workflow Foundation (WF) 啟用工作流程的應用程式。 請參閱 [.NET Framework 中的建置工作流程](http://msdn.microsoft.com/library/cbf3880f-dc7b-466d-b808-1109b1223f4a)。

Windows Forms 類別是一組完整且可重複使用的類型，可大幅簡化 Windows GUI 的開發。 如果要撰寫 ASP.NET Web Form 應用程式，即可使用 Web Form 類別。

## <a name="see-also"></a>另請參閱

[系統需求](../../../docs/framework/get-started/system-requirements.md)   
[安裝指南](../../../docs/framework/install/index.md)   
[開發指南](../../../docs/framework/development-guide.md)   
[工具](../../../docs/framework/tools/index.md)   
[.NET Framework 範例](http://msdn.microsoft.com/library/177055f8-4a1f-43e7-aee6-995c196079b1)   
[.NET Framework 類別庫](http://go.microsoft.com/fwlink/?LinkID=227195)
