---
title: 以 .NET Framework 進行網路追蹤
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework], network tracing
- methods, network tracing
- Networking
- trace enabled debugging
- network tracing, about network tracing
- network tracing
- network, network tracing
- traffic tracing
- tracing [.NET Framework], network
- deploying applications [.NET Framework], network traffic
- capturing network traffic
- Internet, network tracing
- Network Resources
- output, network tracing
- method invocations
ms.assetid: e993b7c3-087f-45d8-9c02-9dded936d804
ms.openlocfilehash: 812fbd0a3f12f9b44e419986b5f3198d95d1e3a7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147407"
---
# <a name="network-tracing-in-the-net-framework"></a>以 .NET Framework 進行網路追蹤
針對方法叫用及 Managed 應用程式所產生的網路流量，.NET Framework 中的網路追蹤能提供對這些相關資訊的存取。 若要為開發中的應用程式進行偵錯，以及分析已部署的應用程式，此功能會非常有用。 您可以自訂網路追蹤所提供的輸出，在程式開發時期和實際執行環境中支援不同的使用案例。  
  
 若要啟用 .NET Framework 中的網路追蹤，您必須為追蹤輸出選取一個目的地，並在應用程式或電腦組態檔中加入網路追蹤組態設定。 如需組態檔和其使用方式的描述，請參閱[組態檔](../../../docs/framework/configure-apps/index.md)。 如需如何啟用網路追蹤的資訊，請參閱[啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)。 如需必須新增至組態檔之設定的資訊，請參閱[如何：設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)。  
  
 啟用追蹤之後，您就可以擷取 **System.Net** 類別所輸出的追蹤資訊。 可產生追蹤資訊的網路類別成員在它們的 .NET Framework 類別庫文件的＜備註＞一節中會包含下面附註：  
  
> [!NOTE]
>  在應用程式中啟用網路追蹤時，這個成員會輸出追蹤資訊。 如需詳細資訊，請參閱＜網路追蹤＞。  
  
## <a name="see-also"></a>請參閱  
 [啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [如何：設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)  
 [解譯網路追蹤](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
[追蹤和檢測應用程式](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
