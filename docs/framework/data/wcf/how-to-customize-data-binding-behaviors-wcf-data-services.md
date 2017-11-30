---
title: "如何：自訂資料繫結行為 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ee72c905ab6df222d256eeeeb2a59579e82923b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>如何：自訂資料繫結行為 (WCF 資料服務)
使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，在從繫結集合新增或移除物件，或偵測到屬性變更時，您可以提供由 <xref:System.Data.Services.Client.DataServiceCollection%601> 呼叫的自訂邏輯。 這個自訂邏輯做為參考的方法<xref:System.Func%602>傳回值的委派`false`時的預設行為仍應執行的自訂方法完成時，`true`當後續的處理事件應該停止。  
  
 本主題中的範例同時向 `entityChanged` 的 `entityCollectionChanged` 和 <xref:System.Data.Services.Client.DataServiceCollection%601> 參數提供自訂方法。 本主題的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立此服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>範例  
 下列 XAML 檔案的程式碼後置頁面會建立 <xref:System.Data.Services.Client.DataServiceCollection%601> 以及自訂方法，當繫結至繫結集合的資料發生變更時會呼叫這些方法。 發生 <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> 事件時，所提供的方法會防止已從繫結集合移除的項目從資料服務中刪除。 發生 <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> 事件時，會驗證 `ShipDate` 值，確保已出貨的訂單不會遭到變更。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>範例  
 下列 XAML 定義上一個範例的視窗。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>另請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
