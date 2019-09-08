---
title: 作法：建立異步 Windows Presentation Framework 應用程式（WCF Data Services）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: 820cb4aa39b49d63cf1acc31e6eb5aa56fd1ba03
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790987"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>作法：建立異步 Windows Presentation Framework 應用程式（WCF Data Services）
使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 時，您可以將從資料服務取得的資料繫結至 Windows Presentation Framework (WPF) 應用程式的 UI 項目。 如需詳細資訊，請參閱[將資料系結至控制項](binding-data-to-controls-wcf-data-services.md)。您也可以使用非同步方式對資料服務執行作業，讓應用程式在等候資料服務要求的回應時繼續回應。 若要透過非同步方式存取資料服務，則需要 Silverlight 應用程式。 如需詳細資訊，請參閱[非同步作業](asynchronous-operations-wcf-data-services.md)。  
  
 本主題說明如何透過非同步方式存取資料服務，並且將結果繫結至 WPF 應用程式的項目。 本主題的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時，會建立此服務和用戶端資料類別。  
  
## <a name="example"></a>範例  
 下列 XAML 定義 WPF 應用程式的視窗。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>範例  
 下列 XAML 檔案的程式碼後置頁面會使用資料服務執行非同步查詢，然後將結果繫結至 WPF 視窗中的項目。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>另請參閱

- [WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)
