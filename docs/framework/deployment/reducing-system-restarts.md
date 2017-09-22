---
title: "在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
caps.latest.revision: 18
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d3f54e3794d1595ed120685a452478791e0ad37c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝程式使用 [重新啟動管理員](http://go.microsoft.com/fwlink/?LinkId=231425) ，盡可能在安裝時防止系統重新啟動。  如果應用程式安裝程式以安裝 .NET Framework，它可能正在使用重新啟動管理員使用這項功能。  如需詳細資訊，請參閱[如何：取得 .NET Framework 4.5 安裝程式的進度](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)。  
  
## 重新啟動電腦的原因  
 假如 .NET Framework 4 應用程式在安裝過程中被使用，[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝需要系統重新啟動。  這是因為在安裝時 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 取代 .NET Framework 4 檔案並需要這些檔案。  透過先偵測和關閉仍在使用中的 .NET Framework 4 應用程式，在大部分情況下重新啟動可以被防止。  不過，有些系統應用程式應該不會關閉。  在這些情況下，就無法避免重新啟動電腦。  
  
## 使用者經驗  
 如果安裝程式偵測到現用 .NET Framework 4 為目標的應用程式，執行 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的完整安裝所提供的使用者也能避免系統重新啟動。  訊息列出所有執行中的 .NET Framework 4 應用程式並提供會在安裝之前關閉這些應用程式的選項。  如果使用者確定，安裝程式會關閉這些應用程式，並能避免重新啟動系統。  如果使用者在很多時間內沒有回應訊息，安裝會繼續，並不關閉任何應用程式。  
  
 如果重新啟動管理員偵測項系統重新啟動，即使執行中的應用程式關閉的條件，就不會顯示任何訊息。  
  
 ![關閉應用程式對話方塊](../../../docs/framework/deployment/media/closeapplicationdialog.png "CloseApplicationDialog")  
提示關閉正在使用的 .NET Framework 應用程式  
  
## 使用鍊結安裝程式  
 如果您想要重新佈署 .NET Framework 與您的應用程式，使用您自己的安裝程式和 UI，則您可以加入 \(鍊結\) .NET Framework 安裝程序 \(chainer\) 的設定程序。  如需這類安裝的詳細資訊，請參閱[開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)。  在鏈結安裝中若要減少系統重新啟動， .NET Framework 安裝程式提供您將應用程式的清單中的安裝程式加入至已關閉。  安裝程式必須透過使用者介面 \(UI\)提供這項資訊提供給使用者，例如訊息方塊取得使用者的回應，然後將回應傳回 .NET Framework 安裝程式。  如需已繫結的安裝程式的範例，請參閱本文 [如何：取得 .NET Framework 4.5 安裝程式的進度](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)。  
  
 如果您使用已繫結的安裝程式，但是您不想提供擁有訊息方塊右邊的應用程式，您可以在命令列 的`/showrmui` 和 `/passive` 選項，將其繫結至 .NET Framework 安裝程序。  當您一起使用這些選項時，安裝程式會顯示關閉的訊息方塊，結束應用程式以避免系統的重新啟動。  此對話方塊的行為與被動模式中使用相同完整的使用者介面下運作。  請參閱[開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)的 .NET Framework 可轉散發套件完整命令列選項。  
  
## 請參閱  
 [部署](../../../docs/framework/deployment/net-framework-and-applications.md)   
 [開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)   
 [如何：取得 .NET Framework 4.5 安裝程式的進度](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)

