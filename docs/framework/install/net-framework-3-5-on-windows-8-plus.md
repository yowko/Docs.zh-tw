---
title: "針對在 Windows 8、Windows 8.1 及 Windows 10 上的 .NET Framework 3.5 安裝進行疑難排解 | Microsoft Docs"
ms.custom: 
ms.date: 04/20/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 3.5, installing on Windows 8
- Windows 8, installing .NET Framework 3.5
ms.assetid: 3eab3eb4-4573-42ac-98f8-36fb2c22c7d5
caps.latest.revision: 69
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: fe9ab371ab8d3eee3778412e446b7aa30b42476b
ms.openlocfilehash: d935648da22db51b004a2f209070bde737a6908d
ms.contentlocale: zh-tw
ms.lasthandoff: 06/02/2017

---

# <a name="installing-the-net-framework-35-on-windows-8-windows-81-and-windows-10"></a>在 Windows 8、Windows 8.1 及 Windows 10 上安裝 .NET Framework 3.5
.NET Framework 是在 Windows 上執行之許多應用程式不可或缺的一部分，提供應用程式執行所需的常見功能。 對於開發人員而言，.NET Framework 提供一個一致的程式設計模型，以便建置應用程式。 如果您使用的是 Windows 作業系統，您的電腦上可能已經安裝了 .NET Framework。 具體來說， [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 會隨附於 [!INCLUDE[win8](../../../includes/win8-md.md)]、 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 會隨附於 [!INCLUDE[win81](../../../includes/win81-md.md)] ，而 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 會隨附於 Windows 10。  
  
 不過，.NET Framework 3.5 不會隨 [!INCLUDE[win8](../../../includes/win8-md.md)]、 [!INCLUDE[win81](../../../includes/win81-md.md)] 或 Windows 10 自動安裝，而必須個別啟用才能執行與其相依的應用程式。 這必須透過 Windows Update (可使用三種方法的其中一種來呼叫) 進行。 所有這些項目都需要網際網路連線：  
  
-   [視需要安裝 .NET Framework 3.5](#OnDemand)  
  
-   [在控制台中啟用 .NET Framework 3.5](#ControlPanel)  
  
-   [下載 .NET Framework 3.5 安裝程式](http://www.microsoft.com/en-us/download/details.aspx?id=21) (注意：這不會直接下載 .NET Framework；它是叫用 Windows Update 的安裝程式)。  
  
 在安裝過程中，您可能會遇到錯誤 0x800f0906、0x800f0907 或 0x800f081f，如果發生這種情況，請參考 [.NET Framework 3.5 安裝錯誤：0x800f0906、0x800f0907 或 0x800f081f](https://support.microsoft.com/en-us/kb/2734782)。 請注意，安裝 [安全性更新 3005628](https://support.microsoft.com/kb/3005628)可能會解決這些問題。  
  
 如果上述任何方法失敗，或者您沒有網際網路連線，則必須使用 Windows 安裝媒體。 如需詳細資訊，請參閱 [.NET Framework 3.5 安裝錯誤文章](https://support.microsoft.com/en-us/kb/2734782)中錯誤 0x800f0906 的方法 3。 如果您沒有安裝媒體，請參閱 [建立 Windows 8.1 的安裝媒體](http://windows.microsoft.com/en-US/windows-8/create-reset-refresh-media?woldogcb=0)。  
  
 重要注意事項：  
  
-   一般而言，請勿解除安裝電腦上的任何 .NET Framework 版本。 不同的應用程式相依於不同版本的 Framework，而一部電腦上可同時載入多種 .NET Framework 版本。  
  
-   針對 2.0 和 3.0 版建置的應用程式也會使用 .NET Framework 3.5。  
  
-   在安裝 .NET Framework 3.5 之前安裝 Windows 語言套件，可能會導致 .NET Framework 3.5 安裝失敗。 在安裝任何 Windows 語言套件之前，請先安裝 .NET Framework 3.5。  
  
-   Windows CardSpace 無法在 [!INCLUDE[win8](../../../includes/win8-md.md)]上搭配 .NET Framework 3.5 使用。  
  
-   由於 .NET Framework 3.5 安裝方式的複雜性，因而無法提供可與 Windows Update 分開執行的個別獨立安裝程式。 同樣地，如果所有其他方法都失敗，就必須求助於安裝媒體 (如前所述)。  
  
<a name="OnDemand"></a>   
## <a name="install-the-net-framework-35-on-demand"></a>視需要安裝 .NET Framework 3.5  
 如果應用程式需要 .NET Framework 3.5，但電腦上找不到已啟用的這個版本，則會在安裝期間或您第一次執行應用程式時顯示下列訊息方塊。 在訊息方塊中，選擇 [ **安裝此功能** ] 啟用 .NET Framework 3.5。 這個選項需要網際網路連線。  
  
 ![在 Windows 8 上安裝 3.5 時顯示的對話方塊](../../../docs/framework/deployment/media/installdialog.png "installdialog")  
  
<a name="ControlPanel"></a>   
## <a name="enable-the-net-framework-35-in-control-panel"></a>在控制台中啟用 .NET Framework 3.5  
 您可以透過 [控制台] 自行啟用 .NET Framework 3.5。 這個選項需要網際網路連線。  
  
1.  按下鍵盤上的 Windows 鍵 ![Windows 標誌](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")，輸入「Windows 功能」，然後按 Enter 鍵。 這會開啟 [開啟或關閉 Windows 功能]  對話方塊。 或者，開啟 [控制台]，並按一下 [程式] 項目，然後按一下 [程式和功能] 下的 [開啟或關閉 Windows 功能]。  
  
2.  選取 [.NET Framework 3.5]  (包括 .NET 2.0 和 3.0) 核取方塊，按下 [確定]，然後在出現提示時重新啟動電腦。  
  
 除非您是需要 WCF 指令碼和處理常式對應功能的開發人員，否則不需要選取 Windows Communication Foundation (WCF) HTTP 啟用的子項目。  
  
 下列影片示範如何執行這項操作：  
  
 ![在 Windows 8 或 8.1 上安裝 .NET Framework](../../../docs/framework/get-started/media/clr-net35-win8.png "CLR_NET35_Win8")  
  
## <a name="see-also"></a>另請參閱  
 [安裝指南](../../../docs/framework/get-started/index.md)

