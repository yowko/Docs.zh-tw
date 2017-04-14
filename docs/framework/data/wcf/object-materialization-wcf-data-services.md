---
title: "物件具體化 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 用戶端程式庫"
  - "WCF Data Services, 查詢"
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 物件具體化 (WCF Data Services)
當您使用 \[**加入服務參考**\] 對話方塊，在 .NET Framework 架構用戶端應用程式中取用 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要時，將會針對資料模型中此摘要所公開的每一個實體類型產生同等的資料類別。  如需詳細資訊，請參閱[產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)。  查詢所傳回之實體資料會具體化為其中一個產生之用戶端資料服務類別的執行個體。  如需追蹤物件之合併選項和識別解析的詳細資訊，請參閱 [管理資料服務內容](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 還能讓您定義自己的用戶端資料服務類別，而不必使用工具產生的資料類別。  這可讓您使用自己的資料類別，也就是「單純的 CLR 物件」\(POCO\) 資料類別。  使用這些自訂資料類別型別時，您應該使用 <xref:System.Data.Services.Common.DataServiceKeyAttribute> 或 <xref:System.Data.Services.Common.DataServiceEntityAttribute> 將資料類別屬性化，並確保用戶端上的型別名稱與資料服務之資料模型中的型別名稱相符。  
  
 程式庫接收查詢回應訊息後，它會將傳回的資料從 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要具體化為用戶端資料服務類別的執行個體，而該執行個體屬於查詢的型別。  具體化這些物件的一般程序如下所示：  
  
1.  用戶端程式庫會從回應訊息摘要中的 `entry` 項目讀取序列化的型別，並嘗試利用下列其中一種方式建立正確型別的新執行個體：  
  
    -   當摘要中宣告的型別所使用的名稱與 <xref:System.Data.Services.Client.DataServiceQuery%601> 的型別使用的名稱相同時，會使用空的建構函式來建立此型別的新執行個體。  
  
    -   當摘要中宣告的型別所使用的名稱與衍生自 <xref:System.Data.Services.Client.DataServiceQuery%601> 的型別所使用的名稱相同時，會利用空的建構函式來建立此衍生型別的新執行個體。  
  
    -   當摘要中宣告的型別與 <xref:System.Data.Services.Client.DataServiceQuery%601> 的型別或任何衍生型別不相符時，會利用空的建構函式來建立所查詢型別的新執行個體。  
  
    -   如果已設定 <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> 屬性，會呼叫提供的委派來覆寫預設的名稱架構型別對應，並建立由 <xref:System.Func%602> 傳回之型別的新執行個體來代替。  如果這個委派傳回 null 值，會建立所查詢型別的新執行個體來代替。  可能必須覆寫預設的名稱架構型別名稱對應來支援繼承案例。  
  
2.  用戶端程式庫會讀取 `entry` 之 `id` 項目的 URI 值，它就是實體的識別值。  除非使用 <xref:System.Data.Services.Client.MergeOption> 的 <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> 值，否則會使用識別值來追蹤 <xref:System.Data.Services.Client.DataServiceContext> 中的物件。  識別值也會用來保證只會建立單一實體執行個體，甚至當某個實體在查詢回應中被傳回多次時也一樣。  
  
3.  用戶端程式庫會讀取摘要項目中的屬性，並在新建立的物件上設定對應的屬性。  當 <xref:System.Data.Services.Client.DataServiceContext> 中已存在與物件所具備之相同的識別值時，會根據 <xref:System.Data.Services.Client.DataServiceContext> 的 <xref:System.Data.Services.Client.MergeOption> 設定來設定屬性。  若某對應的屬性不存在用戶端型別中，則回應可能會包含屬性值。  若發生這種情況，動作會視 <xref:System.Data.Services.Client.DataServiceContext> 的 <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> 屬性而定。  當這個屬性設定為 `true` 時，會忽略遺漏的屬性。  否則，就會引發錯誤。  屬性設定如下所示：  
  
    -   純量屬性會設定為回應訊息之項目中的對應值。  
  
    -   複雜屬性會設定為新的複雜類型執行個體，其會與回應中的複雜類型屬性一起設定。  
  
    -   導覽屬性會傳回相關實體的集合，它們會設定為新的或現有之 <xref:System.Collections.Generic.ICollection%601> 的執行個體，其中 `T` 指相關實體的類型。  除非已將相關物件載入 <xref:System.Data.Services.Client.DataServiceContext>，否則這是一個空的集合。  如需詳細資訊，請參閱[載入延後的內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。  
  
        > [!NOTE]
        >  當產生之用戶端資料類別支援資料繫結時，導覽屬性會傳回 <xref:System.Data.Services.Client.DataServiceCollection%601> 類別的執行個體來代替。  如需詳細資訊，請參閱[將資料繫結至控制項](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)。  
  
4.  便會引發 <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> 事件。  
  
5.  用戶端程式庫會將物件附加至 <xref:System.Data.Services.Client.DataServiceContext>。  當 <xref:System.Data.Services.Client.MergeOption> 為 <xref:System.Data.Services.Client.MergeOption> 時，不會附加物件。  
  
## 請參閱  
 [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)   
 [查詢投影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)