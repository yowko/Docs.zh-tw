---
title: "安全用戶端應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 安全用戶端應用程式
應用程式通常含有許多部分，而這所有的部分都必須受到保護，以免產生漏洞而造成資料遺失，或因其他原因而危及系統。  建立安全的使用者介面可以避免許多問題，因為可以在攻擊者存取資料或系統資源之前就加以防堵。  
  
## 驗證使用者輸入  
 建構存取資料的應用程式時，在證明使用者輸入沒有惡意前，應該假設他們都不懷好意，  否則應用程式可能容易遭到攻擊。  .NET Framework 所包含的類別 \(Class\) 可協助您強制執行輸入控制項的值領域，例如限制可輸入的字元數。  事件攔截程序則可用於撰寫程序以檢查值是否有效。  使用者輸入資料可進行驗證並使用強式型別，以限制應用程式暴露於指令碼和 SQL 插入式攻擊的機會。  
  
> [!IMPORTANT]
>  除了在用戶端應用程式中驗證使用者輸入外，您也必須在資料來源驗證使用者輸入。  攻擊者可能會選擇避開您的應用程式而直接攻擊資料來源。  
  
 [Security and User Input](../../../../docs/standard/security/security-and-user-input.md)  
 說明如何處理涉及使用者輸入而可能具有危險性的細微錯誤。  
  
 [Validating User Input in ASP.NET Web Pages](../Topic/Validating%20User%20Input%20in%20ASP.NET%20Web%20Pages.md)  
 使用 ASP.NET 驗證控制項來驗證使用者輸入的概觀。  
  
 [Windows Form 中的使用者輸入](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 針對在 Windows Form 應用程式中驗證滑鼠及鍵盤輸入而提供連結及資訊。  
  
 [.NET Framework 規則運算式](../../../../docs/standard/base-types/regular-expressions.md)  
 說明如何使用 <xref:System.Text.RegularExpressions.Regex> 類別來檢查使用者輸入的驗證。  
  
## Windows 應用程式  
 以往通常會以完整的使用權限來執行 Windows 應用程式。  .NET Framework 提供的基礎結構可藉由程式碼存取安全性 \(CAS\)，限制在 Windows 應用程式中執行的程式碼。  不過，單靠 CAS 並不足以保護應用程式。  
  
 [Windows Form 安全性](../../../../docs/framework/winforms/windows-forms-security.md)  
 討論如何保護 Windows Form 應用程式並提供相關主題的連結。  
  
 [Windows Form 和 Unmanaged 應用程式](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 說明如何在 Windows Form 應用程式中與 Unmanaged 應用程式互動。  
  
 [ClickOnce Deployment for Windows Forms Applications](http://msdn.microsoft.com/zh-tw/34d8c770-48f2-460c-8d67-4ea5684511df)  
 說明如何在 Windows Form 應用程式中使用 `ClickOnce` 部署，並討論安全性含意。  
  
## ASP.NET 和 XML Web Service  
 ASP.NET 應用程式通常需要限制網站某部份的存取，並提供其他機制以保護資料和網站安全性。  這些連結提供保護 ASP.NET 應用程式的有用資訊。  
  
 XML Web Service 所提供的資料可由 ASP.NET 應用程式、Windows Form 應用程式或其他 Web 服務使用。  除了管理 Web 服務本身的安全性外，也需要管理用戶端應用程式的安全性。  
  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------|--------|  
|[NIB: ASP.NET Security](http://msdn.microsoft.com/zh-tw/04b37532-18d9-40b4-8e5f-ee09a70b311d)|討論如何保護 ASP.NET 應用程式。|  
|[Securing XML Web Services Created Using ASP.NET](http://msdn.microsoft.com/zh-tw/354b2ab1-2782-4542-b32a-dc560178b90c)|討論如何實作 ASP.NET Web 服務的安全性。|  
|[Script Exploits Overview](../Topic/Script%20Exploits%20Overview.md)|說明如何防堵指令碼式攻擊，此類攻擊會嘗試在網頁中插入惡意的字元。|  
|[NIB:Basic Security Practices for ASP.NET Web Applications](http://msdn.microsoft.com/zh-tw/94a52ab8-731d-417e-b997-721baf43df38)|一般安全性資訊以及進階討論區的連結。|  
  
## 遠端處理  
 .NET 遠端處理可讓您輕鬆建置四處分散的應用程式，不論應用程式元件全都集中在同一台電腦或散佈在全世界各個角落。  您可以建置用戶端應用程式，讓它們使用相同電腦 \(或其網路上可連接的任何其他電腦\) 上其他處理序中的物件。  也可以使用 .NET 遠端處理，與同一處理序中的其他應用程式定義域通訊。  
  
|資源|描述|  
|--------|--------|  
|[Configuration of Remote Applications](http://msdn.microsoft.com/zh-tw/92c0c097-d984-4315-835b-7490ecdf1097)|討論如何設定遠端處理應用程式以避免常見問題。|  
|[Security in Remoting](http://msdn.microsoft.com/zh-tw/9574262c-d4b1-41c5-8600-24ff147c0add)|說明驗證和加密，以及與遠端處理相關的其他安全性主題。|  
|[Security and Remoting Considerations](../../../../docs/framework/misc/security-and-remoting-considerations.md)|說明受保護的物件和跨應用程式定義域的安全性問題。|  
  
## 請參閱  
 [保護 ADO.NET 應用程式](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [Recommendations for Data Access Strategies](http://msdn.microsoft.com/zh-tw/72411f32-d12a-4de8-b961-e54fca7faaf5)   
 [設定應用程式的安全性](../Topic/Securing%20Applications.md)   
 [保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)