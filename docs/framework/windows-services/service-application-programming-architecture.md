---
title: 服務應用程式的程式設計架構
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
author: ghogen
ms.openlocfilehash: d5dc690cfe460be79251d60850319e5232379f3c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935447"
---
# <a name="service-application-programming-architecture"></a>服務應用程式的程式設計架構
Windows 服務應用程式會以繼承自 <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> 類別的類別為基礎。 您會覆寫來自這個類別的方法，並定義適用於它們的功能以決定服務的行為方式。  
  
 以下是涉及服務建立的主要類別：  
  
- <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>：您會在建立服務並定義程式碼以決定服務如何在此繼承類別中運作時，覆寫來自 <xref:System.ServiceProcess.ServiceBase> 類別的方法。  
  
- <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> 和 <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType>：您會使用這些類別來安裝和解除安裝服務。  
  
 此外，名為 <xref:System.ServiceProcess.ServiceController> 的類別可用來操作服務本身。 這個類別並未涉及服務的建立，但可用來啟動和停止服務、將命令傳遞到其中，以及傳回一連串的列舉。  
  
## <a name="defining-your-services-behavior"></a>定義服務行為  
 在服務類別中，您會覆寫基底類別函式，以決定在服務控制管理員中變更服務狀態時會發生什麼事。 <xref:System.ServiceProcess.ServiceBase> 類別會公開下列方法，您可以覆寫這些方法以加入自訂行為。  
  
|方法|覆寫到|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|表示當服務開始執行時應該採取的動作。 您必須在此程序中為服務撰寫程式碼以執行有用的工作。|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|表示服務暫停時應該會發生什麼事。|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|表示服務停止執行時應該會發生什麼事。|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|表示當服務在暫停之後繼續正常運作時應該會發生什麼事。|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|表示如果服務在系統關機時正在執行，則在系統關機之前應該會發生什麼事。|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|表示當服務接收到自訂命令時應該會發生什麼事。 如需自訂命令的詳細資訊，請參閱 MSDN Online。|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|表示在接收到電源管理事件 (例如電力偏低或暫停作業) 時服務應如何回應。|  
  
> [!NOTE]
> 這些方法表示服務在其存留期間行進的狀態；服務會從某個狀態轉換到下一個狀態。 例如，您絕對不會讓服務在呼叫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 之前回應 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 命令。  
  
 還有其他數個感興趣的屬性和方法。 它們包括：  
  
- <xref:System.ServiceProcess.ServiceBase> 類別上的 <xref:System.ServiceProcess.ServiceBase.Run%2A> 方法。 這是服務的主要進入點。 當您使用 Windows 服務範本建立服務時，會將程式碼插入應用程式的 `Main` 方法來執行服務。 此程式碼如下所示：  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    > 這些範例會使用 <xref:System.ServiceProcess.ServiceBase> 類型的陣列，應用程式所包含的每個服務均可加入到此陣列，接著可一起執行所有服務。 不過，如果您只建立單一服務，則可以選擇不使用陣列，而只宣告繼承自 <xref:System.ServiceProcess.ServiceBase> 的新物件，然後加以執行。 如需範例，請參閱[如何：以程式設計方式撰寫服務](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)。  
  
- <xref:System.ServiceProcess.ServiceBase> 類別上的一系列屬性。 這些屬性會決定可在您的服務上呼叫哪些方法。 例如，將 <xref:System.ServiceProcess.ServiceBase.CanStop%2A> 屬性設定為 `true` 時，可以呼叫服務上的 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法。 將 <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> 屬性設定為 `true` 時，可以呼叫 <xref:System.ServiceProcess.ServiceBase.OnPause%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 方法。 當您將這其中一個屬性設定為 `true` 時，接著應該覆寫並定義適用於相關聯方法的處理。  
  
    > [!NOTE]
    > 您的服務至少必須覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A>，才能發揮作用。  
  
 您也可以使用名為 <xref:System.ServiceProcess.ServiceController> 的元件進行通訊，並控制現有服務的行為。  
  
## <a name="see-also"></a>另請參閱

- [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)
