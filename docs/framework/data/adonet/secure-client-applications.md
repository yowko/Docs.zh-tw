---
title: 保護用戶端應用程式的安全
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: a3b035d59a39ca20f6a81fbd40d39069a7cc43c2
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46706287"
---
# <a name="secure-client-applications"></a>保護用戶端應用程式的安全
應用程式通常含有許多部分，而這所有的部分都必須受到保護，以免產生漏洞而造成資料遺失，或因其他原因而危及系統。 建立安全的使用者介面可以避免許多問題，因為可以在攻擊者存取資料或系統資源之前就加以防堵。  
  
## <a name="validate-user-input"></a>驗證使用者輸入  
 建構存取資料的應用程式時，在證明使用者輸入沒有惡意前，應該假設他們都不懷好意， 否則應用程式可能容易遭到攻擊。 .NET Framework 所包含的類別 (Class) 可協助您強制執行輸入控制項的值領域，例如限制可輸入的字元數。 事件攔截程序則可用於撰寫程序以檢查值是否有效。 使用者輸入資料可進行驗證並使用強式型別，以限制應用程式暴露於指令碼和 SQL 插入式攻擊的機會。  
  
> [!IMPORTANT]
>  除了在用戶端應用程式中驗證使用者輸入外，您也必須在資料來源驗證使用者輸入。 攻擊者可能會選擇避開您的應用程式而直接攻擊資料來源。  
  
 [安全性和使用者輸入](../../../../docs/standard/security/security-and-user-input.md)  
 說明如何處理涉及使用者輸入而可能具有危險性的細微錯誤。  
  
 [ASP.NET Web Pages 中驗證使用者輸入](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 使用 ASP.NET 驗證控制項來驗證使用者輸入的概觀。  
  
 [Windows Forms 中的使用者輸入](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 針對在 Windows Forms 應用程式中驗證滑鼠及鍵盤輸入而提供連結及資訊。  
  
 [.NET Framework 規則運算式](../../../../docs/standard/base-types/regular-expressions.md)  
 說明如何使用 <xref:System.Text.RegularExpressions.Regex> 類別來檢查使用者輸入的驗證。  
  
## <a name="windows-applications"></a>Windows 應用程式  
 以往通常會以完整的使用權限來執行 Windows 應用程式。 .NET Framework 提供的基礎結構可藉由程式碼存取安全性 (CAS)，限制在 Windows 應用程式中執行的程式碼。 不過，單靠 CAS 並不足以保護應用程式。  
  
 [Windows Forms 安全性](../../../../docs/framework/winforms/windows-forms-security.md)  
 討論如何保護 Windows Forms 應用程式並提供相關主題的連結。  
  
 [Windows Forms 和 Unmanaged 應用程式](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 說明如何在 Windows Forms 應用程式中與 Unmanaged 應用程式互動。  
  
 [ClickOnce 部署的 Windows Forms 應用程式](https://msdn.microsoft.com/library/34d8c770-48f2-460c-8d67-4ea5684511df)  
 說明如何在 Windows Form 應用程式中使用 `ClickOnce` 部署，並討論安全性含意。  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET 和 XML Web Service  
 ASP.NET 應用程式通常需要限制網站某部份的存取，並提供其他機制以保護資料和網站安全性。 這些連結提供保護 ASP.NET 應用程式的有用資訊。  
  
 XML Web Service 所提供的資料可由 ASP.NET 應用程式、Windows Form 應用程式或其他 Web 服務使用。 除了管理 Web 服務本身的安全性外，也需要管理用戶端應用程式的安全性。  
  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[NIB: ASP.NET 安全性](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d)|討論如何保護 ASP.NET 應用程式。|  
|[保護使用 ASP.NET 建立 XML Web Service](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c)|討論如何實作 ASP.NET Web 服務的安全性。|  
|[指令碼攻擊概觀](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|說明如何防堵指令碼式攻擊，此類攻擊會嘗試在網頁中插入惡意的字元。|  
|[NIB： 基本的 ASP.NET Web 應用程式的安全性作法](https://msdn.microsoft.com/library/94a52ab8-731d-417e-b997-721baf43df38)|一般安全性資訊以及進階討論區的連結。|  
  
## <a name="remoting"></a>遠端處理  
 .NET 遠端處理可讓您輕鬆建置四處分散的應用程式，不論應用程式元件全都集中在同一台電腦或散佈在全世界各個角落。 您可以建置用戶端應用程式，讓它們使用相同電腦 (或其網路上可連接的任何其他電腦) 上其他處理序中的物件。 也可以使用 .NET 遠端處理，與同一處理序中的其他應用程式定義域通訊。  
  
|資源|描述|  
|--------------|-----------------|  
|[遠端應用程式的組態](https://msdn.microsoft.com/library/92c0c097-d984-4315-835b-7490ecdf1097)|討論如何設定遠端處理應用程式以避免常見問題。|  
|[遠端處理中的安全性](https://msdn.microsoft.com/library/9574262c-d4b1-41c5-8600-24ff147c0add)|說明驗證和加密，以及與遠端處理相關的其他安全性主題。|  
|[安全性和遠端處理考量](../../../../docs/framework/misc/security-and-remoting-considerations.md)|說明受保護的物件和跨應用程式定義域的安全性問題。|  
  
## <a name="see-also"></a>另請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [資料存取策略的建議](https://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [設定應用程式的安全性](/visualstudio/ide/securing-applications)  
 [保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
