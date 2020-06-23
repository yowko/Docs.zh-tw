---
title: Windows Communication Foundation 繫結概觀
description: 瞭解系結，其會指定如何連接到 WCF 服務，包括系結的元素，以及如何指定服務端點的系結。
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: da8050c4e9aeb111de3a54315b3650bcf09f23ed
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247710"
---
# <a name="windows-communication-foundation-bindings-overview"></a>Windows Communication Foundation 繫結概觀
系結是用來指定連接到 Windows Communication Foundation （WCF）服務端點所需之通訊詳細資料的物件。 WCF 服務中的每個端點都需要正確指定的繫結。 本主題概述系結所定義的通訊詳細資料類型、系結的元素、WCF 中包含的系結，以及如何為端點指定系結。  
  
## <a name="what-a-binding-defines"></a>繫結所定義的內容  
 繫結中的資訊可能很基本，也可能很複雜。 最基本的繫結只會指定連線至端點時必須使用的傳輸通訊協定 (例如 HTTP)。 一般來說，系結所包含關於如何連接到端點的資訊，屬於下列其中一個類別：  
  
 **通訊協定**  
 判斷使用的安全性機制：可靠的傳訊能力或異動內容流量設定。  
  
 **編碼方式**  
 判斷訊息的編碼方式 (例如，文字或二進位)。  
  
 **傳輸**  
 判斷要使用的基礎傳輸通訊協定 (例如，TCP 或 HTTP)。  
  
## <a name="the-elements-of-a-binding"></a>繫結項目  
 繫結基本上是由排列順序的繫結項目堆疊所組成，而每個繫結項目都會指定連線至服務端點時所需的部分通訊資訊。 堆疊中最低的那兩層為必要項。 堆疊基底是傳輸繫結項目，而這個項目的正上方是其中含有訊息編碼規格的項目。 指定其他通訊協定的選用繫結程序元素則會置於這兩個必要元素之上。 如需這些繫結項目和其正確順序的詳細資訊，請參閱[自訂](./extending/custom-bindings.md)系結。  
  
## <a name="system-provided-bindings"></a>系統提供的繫結  
 繫結中的資訊可能很複雜，而有些設定也可能彼此不相容。 基於這個理由，WCF 會包含一組系統提供的系結。 這些繫結程序設計為滿足大多數應用程式需求。 下列類別則表示系統提供之繫結的一些範例：  
  
- <xref:System.ServiceModel.BasicHttpBinding>：一種 HTTP 通訊協定繫結，可用於連線至 Web 服務，並符合 WS-I Basic Profile 規格 (例如，以 ASP.NET Web 服務為基礎的服務)。  
  
- <xref:System.ServiceModel.WSHttpBinding>：一種互通的繫結，可用於連線至符合 WS-* 通訊協定的端點。  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>：使用 .NET Framework 連接至同一部電腦上的其他 WCF 端點。  
  
- <xref:System.ServiceModel.NetMsmqBinding>：使用 .NET Framework 來建立與其他 WCF 端點的佇列訊息連接。  

- <xref:System.ServiceModel.NetTcpBinding>：此系結提供的效能高於 HTTP 系結，且非常適合在區域網路中使用。
  
 如需所有 WCF 提供之系結的完整清單和描述，請參閱[系統提供](system-provided-bindings.md)的系結。  
  
## <a name="using-your-own-bindings"></a>使用您自己的繫結  
 如果所含之系統提供的繫結都沒有服務應用程式需要的正確功能組合，您可以建立自己的繫結。 做法有二種。 您可以使用 <xref:System.ServiceModel.Channels.CustomBinding> 物件從已存在的繫結元素中建立新的繫結，或者藉由從 <xref:System.ServiceModel.Channels.Binding> 繫結衍生，而建立完整的使用者定義繫結。 如需使用這兩種方法建立您自己的系結的詳細資訊，請參閱[自訂](./extending/custom-bindings.md)系結和[建立使用者定義](./extending/creating-user-defined-bindings.md)系結。  
  
## <a name="using-bindings"></a>使用繫結  
 使用繫結牽涉到兩個基本步驟：  
  
1. 選取或定義繫結。 最簡單的方法是選擇包含在 WCF 中的其中一個系統提供系結，並將其與預設設定搭配使用。 也可以選擇系統提供的繫結程序，並重設其屬性值以符合您的需求。 此外，您可以建立自訂繫結或使用者定義的繫結，以對這些繫結擁有更高程度的控制權和自訂權。  
  
2. 建立使用已選取或已定義之繫結的端點。  
  
## <a name="code-and-configuration"></a>程式碼和組態  
 有兩種方法可讓您定義繫結：透過程示碼或透過組態。 這兩個方法與您是使用系統提供的繫結或自訂繫結無關。 一般來說，使用程式碼可讓您在設計階段時完全控制繫結的定義。 另一方面，使用設定可讓 WCF 服務或用戶端的系統管理員或使用者變更系結的參數，而不需要重新編譯服務應用程式。 這種彈性通常是理想的做法，因為沒有辦法可以預測要部署 WCF 應用程式的特定電腦需求。 將繫結 (和位址) 資訊留在程式碼外面，可在不需要重新編譯或重新部署應用程式的情況下，就可以變更繫結和位址資訊。 請注意，會先建立在組態中指定繫結，之後才建立在程式碼中定義的繫結，這樣可讓程式碼定義的繫結覆寫任何組態定義的繫結。  
  
## <a name="see-also"></a>另請參閱

- [使用繫結設定服務與用戶端](using-bindings-to-configure-services-and-clients.md)
