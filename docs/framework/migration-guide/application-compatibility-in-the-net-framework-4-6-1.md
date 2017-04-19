---
title: ".NET Framework 4.6.1 中的應用程式相容性 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility,.NET Framework
- application compatibility,.NET Framework 4.6.1
ms.assetid: b86cc4ad-6a9e-4246-aa96-5aae319d9d55
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 95c8e4d38a9a4770813db141d76d33e10e34cc12
ms.lasthandoff: 04/18/2017

---
# <a name="application-compatibility-in-the-net-framework-461"></a>.NET Framework 4.6.1 中的應用程式相容性
本主題提供 .NET Framework 4.6 與 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 間之應用程式相容性問題的資訊連結。 問題分為兩類：  
  
 [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-1.md)  
 執行階段變更影響在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 下執行並使用特定功能的所有應用程式。  
  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)  
 重定目標變更只會影響特別以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標來重新編譯的應用程式。 針對舊版 .NET Framework 之應用程式的行為，就像是在這些版本下執行的行為一樣。  
  
 在描述執行階段變更和重定目標變更的項目中，我們依每個項目的預期影響將項目分類如下：  
  
 主要  
 這是影響大量應用程式或需要大幅修改程式碼的重大變更。  
  
 次要  
 這是影響少量應用程式或需要稍微修改程式碼的變更。  
  
 邊緣案例  
 這是在非常特定 (罕見) 的情況下影響應用程式的變更。  
  
 透明  
 此變更對應用程式的開發人員或使用者的影響不明顯。 發生此變更的應用程式應該不需要修改。  
  
## <a name="see-also"></a>另請參閱  
 [應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md)
