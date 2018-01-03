---
title: "安全存取資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 07892869759ac5856b26099f2421caff1ebaf74d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="secure-data-access"></a>安全存取資料
若要撰寫安全的 ADO.NET 程式碼，您必須了解基礎資料存放區或資料庫中可用的安全性機制。 您也需要考量您的應用程式所可能包含的其他功能或元件的安全性隱含。  
  
## <a name="authentication-authorization-and-permissions"></a>驗證、授權和權限  
 在連接 Microsoft SQL Server 時，您也可以選擇使用「Windows 驗證」(也稱為「整合式安全性」)，它使用目前使用中的 Windows 使用者識別，而非傳遞使用者 ID 和密碼。 強烈建議您使用「Windows 驗證」，因為使用者認證並不會在連接字串中公開 (Expose)。 如果無法使用「Windows 驗證」連接到 SQL Server，則請考慮使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 在執行階段建立連接字串。  
  
 根據應用程式類型，需要以不同方式處理驗證所使用的認證。 例如，在 Windows Form 應用程式中，系統會提示使用者提供驗證資訊，或可使用使用者的 Windows 認證。 不過，Web 應用程式通常使用應用程式本身 (而非使用者) 提供的認證來存取資料。  
  
 使用者一旦經過驗證，其動作範圍就會根據所授與的權限而定。 請務必遵守最小權限的原則，並僅授與絕對必要的權限。  
  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)|描述保護連接資訊的安全性最佳作法和技術，例如使用受保護的組態來加密連接字串。|  
|[資料存取策略的建議](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)|提供存取資料及執行資料庫作業的建議。|  
|[連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)|說明如何在執行階段從使用者輸入建立連接字串。|  
|[SQL Server 安全性概觀](../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)|說明 SQL Server 安全性架構。|  
  
## <a name="parameterized-commands-and-sql-injection"></a>參數型命令和 SQL 插入  
 使用參數型命令 (Parameterized Command) 有助於防衛 SQL 插入式攻擊，在此類攻擊中，攻擊者會將命令「插入」至 SQL 陳述式而危及伺服器的安全。 參數型命令可確保自外部來源所接收的值僅會以值的形式傳遞，而不會當做 Transact-SQL 陳述式，藉此防衛 SQL 插入式攻擊。 因此，已插入值的 Transact-SQL 命令不會在資料來源執行， 而是將其做為參數值單獨評估。 除了安全性優點外，參數型命令也提供方便的方法，可您安排以 Transact-SQL 陳述式傳遞的值或傳遞到預存程序 (Stored Procedure) 的值。  
  
 如需有關使用參數型命令的詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[DataAdapter 參數](../../../../docs/framework/data/adonet/dataadapter-parameters.md)|說明如何將參數搭配 `DataAdapter` 使用。|  
|[使用預存程序修改資料](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)|說明如何指定參數並取得傳回值。|  
|[在 SQL Server 中使用預存程序來管理權限](../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)|說明如何使用 SQL Server 預存程序以封裝資料存取。|  
  
## <a name="script-exploits"></a>指令碼攻擊  
 指令碼攻擊是另一種形式的插入，此種攻擊會使用插入至網頁的惡意字元。 瀏覽器並不會驗證插入的字元，而會將其當做網頁的一部分來處理。  
  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[指令碼擅用概觀](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|說明如何防衛指令碼和 SQL 陳述式攻擊。|  
  
## <a name="probing-attacks"></a>探查攻擊  
 攻擊者通常利用例外狀況的資訊，例如伺服器、資料庫或資料表名稱，來對系統設置攻擊。 由於例外狀況可能包含有關應用程式或資料來源的特定資訊，所以您可以只將必要的資訊公開給用戶端，使應用程式和資料來源有更嚴密的保護。  
  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[例外狀況處理基本概念](../../../../docs/standard/exceptions/exception-handling-fundamentals.md)|說明 try/catch/finally 結構化例外狀況處理 (Structured Exception Handling) 的基本形式。|  
|[例外狀況的最佳做法](../../../../docs/standard/exceptions/best-practices-for-exceptions.md)|說明處理例外狀況的最佳做法。|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>保護 Microsoft Access 和 Excel 資料來源  
 當安全性需求為最低或不存在時，可將 Microsoft Access 和 Microsoft Excel 當做 ADO.NET 應用程式的資料存放區。 其安全性功能可有效遏止侵擾，但僅止於阻擋狀況外使用者的干擾。 Access 和 Excel 的實體資料檔存在於檔案系統中，而且必須讓所有的使用者都可以存取。 這使得這些檔案易遭受因竊取或資料遺失而導致的攻擊，因為檔案可以輕易地複製或變更。 在需要強固安全性時，請使用 SQL Server 或其他伺服器架構的資料庫，因為其中的實體資料檔是無法從檔案系統讀取的。  
  
 如需有關保護 Access 和 Excel 資料的詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[安全性考量和 Access 2007 的指引](http://go.microsoft.com/fwlink/?LinkId=98354)|說明 Access 2007 的安全性技巧，例如加密檔案、管理密碼、將資料庫轉換為新的 ACCDB 和 ACCDE 格式，以及使用其他的安全性選項。|  
|[協助保護 Access 資料庫與使用者層級安全性 (MDB)](http://go.microsoft.com/fwlink/?LinkId=47697)|適用於 Access 2003。 提供實作使用者層級安全性以保護 Access 2003 資料的指示。|  
|[了解工作群組資訊檔的角色中存取安全性](http://support.microsoft.com/kb/305542)|說明 Access 2003 安全性中的工作群組資訊檔的角色和關係。|  
|[經常詢問問題相關的 Microsoft Access 安全性 Microsoft Access 2.0 到 2000年版](http://go.microsoft.com/fwlink/?LinkId=47698)|可下載版本的 Microsoft Access 安全性常見問題集。|  
|[安全性和防護疑難排解](http://go.microsoft.com/fwlink/?LinkId=47703)|呈現 Excel 2003 一般安全性問題的解決方案。|  
  
## <a name="enterprise-services"></a>企業服務  
 COM+ 本身包含根據 Windows NT 帳戶和處理序/執行緒模擬而定的安全性模型。 <xref:System.EnterpriseServices> 命名空間提供包裝函式，這些包裝函式允許 .NET 應用程式透過 <xref:System.EnterpriseServices.ServicedComponent> 類別來整合 Managed 程式碼與 COM+ 安全性服務。  
  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[COM + 角色為基礎的安全性和.NET Framework](http://msdn.microsoft.com/en-us/02ab22ef-e5e2-4d29-b33a-6e03d94c4981)|討論如何整合 Managed 程式碼和 COM+ 安全性服務。|  
  
## <a name="interoperating-with-unmanaged-code"></a>與 Unmanaged 程式碼互通  
 .NET Framework 可用於與 Unmanaged 程式碼互動，這包括 COM 元件、COM+ 服務、外部型別程式庫以及許多作業系統服務。 使用 Unmanaged 程式碼時需要越過 Managed 程式碼的安全性範疇。 您的程式碼以及它所呼叫的任何程式碼，都必須具備 Unmanaged 程式碼權限 (指定了 <xref:System.Security.Permissions.SecurityPermission> 旗標的 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>)。 Unmanaged 程式碼可能會在應用程式中引入非預期的安全性漏洞； 因此，除非絕對必要，否則應該避免與 Unmanaged 程式碼互通。  
  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[與 Unmanaged 程式碼互通](../../../../docs/framework/interop/index.md)|包含說明如何將 COM 元件公開至 .NET Framework 以及如何將 .NET Framework 元件公開至 COM 的主題。|  
|[進階 COM 互通性](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)|包含主要 Interop 組件 (Assembly)、執行緒和自訂封送處理 (Marshaling) 等進階主題。|  
  
## <a name="see-also"></a>請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server 安全性](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [資料存取策略的建議](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
