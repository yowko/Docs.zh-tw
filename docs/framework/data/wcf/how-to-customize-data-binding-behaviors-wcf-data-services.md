---
title: 如何：自訂資料繫結行為 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: 13847923a5f31108e93ef12cf7775109be3cd9eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172511"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>如何：自訂資料繫結行為 (WCF 資料服務)

使用 WCF Data Services 時，您可以提供在系結 <xref:System.Data.Services.Client.DataServiceCollection%601> 集合中加入或移除物件，或偵測到屬性變更時，所呼叫的自訂邏輯。 這個自訂邏輯會以方法的形式提供，這些方法是以委派的形式來傳回，當 <xref:System.Func%602> `false` 自訂方法完成時，以及後續的 `true` 事件處理應該停止時，就會傳回的值。  
  
 本主題中的範例同時向 `entityChanged` 的 `entityCollectionChanged` 和 <xref:System.Data.Services.Client.DataServiceCollection%601> 參數提供自訂方法。 本主題的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](quickstart-wcf-data-services.md)時建立。  
  
## <a name="example"></a>範例  

 下列 XAML 檔案的程式碼後置頁面會建立 <xref:System.Data.Services.Client.DataServiceCollection%601> 以及自訂方法，當繫結至繫結集合的資料發生變更時會呼叫這些方法。 發生 <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> 事件時，所提供的方法會防止已從繫結集合移除的項目從資料服務中刪除。 發生 <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> 事件時，會驗證 `ShipDate` 值，確保已出貨的訂單不會遭到變更。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>範例  

 下列 XAML 定義上一個範例的視窗。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>另請參閱

- [WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)
