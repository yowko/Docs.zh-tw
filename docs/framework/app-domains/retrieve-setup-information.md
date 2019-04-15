---
title: 從應用程式定義域擷取安裝資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80c9fe6de0fca86497ffe84cd8dadf0eb8cef6c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108949"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a>從應用程式定義域擷取安裝資訊
每個應用程式定義域的執行個體都包含這兩個屬性及 <xref:System.AppDomainSetup> 資訊。 您可以從使用 <xref:System.AppDomain?displayProperty=nameWithType> 類別的應用程式定義域擷取安裝資訊。 這個類別提供數個成員，它們會擷取應用程式定義域的組態資訊。  
  
 您也可以查詢應用程式定義域的 **AppDomainSetup** 物件，取得在建立時即已傳遞至定義域的安裝資訊。  
  
 下例會建立新的應用程式定義域，然後將數個成員值列印到主控台。  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 然後，下列範例集會擷取應用程式定義域的安裝資訊。 請注意，`AppDomain.SetupInformation.ApplicationBase` 取得組態資訊。  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [使用應用程式定義域設計程式](application-domains.md#programming-with-application-domains)
- [使用應用程式定義域](../../../docs/framework/app-domains/use.md)
