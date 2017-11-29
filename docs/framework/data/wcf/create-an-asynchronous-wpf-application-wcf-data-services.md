---
title: "如何：建立非同步 Windows Presentation Framework 應用程式 (WCF 資料服務)"
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
helpviewer_keywords: WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 351812d632a394612e8ea241b7fea388066b4199
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>如何：建立非同步 Windows Presentation Framework 應用程式 (WCF 資料服務)
使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 時，您可以將從資料服務取得的資料繫結至 Windows Presentation Framework (WPF) 應用程式的 UI 項目。 如需詳細資訊，請參閱[資料繫結至控制項](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)。您也可以執行對資料服務作業以非同步的方式，讓應用程式繼續等候資料服務要求的回應時回應。 若要透過非同步方式存取資料服務，則需要 Silverlight 應用程式。 如需詳細資訊，請參閱[非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)。  
  
 本主題說明如何透過非同步方式存取資料服務，並且將結果繫結至 WPF 應用程式的項目。 本主題的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立此服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>範例  
 下列 XAML 定義 WPF 應用程式的視窗。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>範例  
 下列 XAML 檔案的程式碼後置頁面會使用資料服務執行非同步查詢，然後將結果繫結至 WPF 視窗中的項目。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>另請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
