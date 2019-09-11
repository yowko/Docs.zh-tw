---
title: Entity Framework 提供者 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 5a40eeafafef56902a9ae5037e6bc946b598f752
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854089"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Entity Framework 提供者 (WCF 資料服務)
如同 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 一般，ADO.NET Entity Framework 是以實體資料模型為基礎 (實體資料模型是一種實體關聯模型)。 Entity Framework 會根據對資料來源的對等作業，將作業轉譯為其實體資料模型（稱為*概念模型*）的執行。 因此，Entity Framework 非常適合做為以關聯式資料為基礎之資料服務的提供者，而且只要資料庫具有支援 Entity Framework 的資料提供者，皆可與 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 搭配使用。 如需目前支援 Entity Framework 的資料來源清單，請參閱 Entity Framework 的[協力廠商提供者](https://go.microsoft.com/fwlink/?LinkId=143699)。  
  
 在概念模型中，實體容器是服務的根。 您必須先在 Entity Framework 中定義概念模型，資料服務才能公開資料。 如需詳細資訊，請參閱[如何：使用 ADO.NET Entity Framework 資料來源](create-a-data-service-using-an-adonet-ef-data-wcf.md)建立資料服務。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]支援開放式平行存取模型，可讓您定義實體的並行標記。 這個並行語彙基元包含實體的一個或多個屬性，資料服務會使用它來判斷正在要求、更新或刪除的資料中是否已經發生變更。 當取自要求中 eTag 的語彙基元值與目前實體的值不同時，資料服務就會引發例外狀況。 若要指出屬性是並行標記的一部分，您必須在 Entity Framework 提供者所`ConcurrencyMode="Fixed"`定義的資料模型中套用屬性。 並行語彙基元不得包含索引鍵屬性或導覽屬性。 如需詳細資訊，請參閱[更新資料服務](updating-the-data-service-wcf-data-services.md)。  
  
 若要深入瞭解 Entity Framework，請參閱[Entity Framework 總覽](../adonet/ef/overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [資料服務提供者](data-services-providers-wcf-data-services.md)
- [反映提供者](reflection-provider-wcf-data-services.md)
- [實體資料模型](../adonet/entity-data-model.md)
