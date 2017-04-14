---
title: "在 ASP.NET 中使用 System.Transactions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 在 ASP.NET 中使用 System.Transactions
本主題說明如何成功運用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式中的 <xref:System.Transactions>。  
  
## 啟用 ASP.NET 中的 DistributedTransactionPermission  
 <xref:System.Transactions> 支援部分信任的呼叫端，並且含有 **AllowPartiallyTrustedCallers** 屬性 \(APTCA\) 標記。<xref:System.Transactions> 會依據 <xref:System.Transactions> 所公開的資源型別 \(例如，系統記憶體、共用的整個處理序資源、整個系統資源與其他資源\)，以及存取這些資源時必要的信任層級來共同定義信任層級。 在部分信任的環境中，非完整信任組件只能使用應用程式定義域內的交易 \(在此情況下，系統記憶體是唯一受保護的資源\)，除非它被授予了 <xref:System.Transactions.DistributedTransactionPermission>。  
  
 每當交易的管理擴大至需由「Microsoft 分散式交易協調器」\(MSDTC\) 管理的情況時，就會要求 <xref:System.Transactions.DistributedTransactionPermission>。 這種情況會使用整個處理序的資源，特別是全域資源 \(亦即在 MSDTC 記錄中保留的空格\)。 資料庫的 Web 前端或是將資料庫當成所提供的服務一部分來使用的應用程式，都是這類用法的例子。  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 擁有專屬的信任層級，並透過原則檔將這些信任層級關聯至特定的權限。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [ASP.NET Trust Levels and Policy Files](../Topic/ASP.NET%20Trust%20Levels%20and%20Policy%20Files.md). 在您初次安裝 Windows SDK 時，沒有任何預設的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 原則檔會與 <xref:System.Transactions.DistributedTransactionPermission> 關聯。 因此，當 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式中的交易規模擴大至需由 MSDTC 管理時，在要求 <xref:System.Transactions.DistributedTransactionPermission> 時，擴大規模會失敗，並傳回 <xref:System.Security.SecurityException>。 若要在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 部分信任環境中啟用交易擴大規模，您應該在同一個預設信任層級中授與 <xref:System.Transactions.DistributedTransactionPermission> 權限 \(與在 <xref:System.Data.SqlClient.SqlClientPermission> 中所授與的權限一樣\)。 您可以選擇設定自訂的信任層級與原則檔來支援這項作業，或者也可以修改預設的原則檔，亦即 **Web\_hightrust.config** 和 **Web\_mediumtrust.config**。  
  
 若要修改原則檔，請將 **DistributedTransactionPermission** 的 **SecurityClass** 項目加入 **PolicyLevel** 項目底下的 **SecurityClasses** 項目中，並將對應的 **IPermission** 項目加入 System.Transactions 的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** 底下。 下列組態檔示範如何進行。  
  
```  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 安全性原則，請參閱 [securityPolicy 項目 \(ASP.NET 設定結構描述\)](http://msdn.microsoft.com/zh-tw/469d8d22-d263-46bb-8400-40d8d027faba)。  
  
## 動態編譯  
 如果您希望匯入並使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式中的 <xref:System.Transactions> \(在存取時動態編譯\)，您可以在組態檔中放置 <xref:System.Transactions> 組件的參考。 具體來說，您應該將參考加入預設根 **Web.config** 組態檔，或是特定 Web 應用程式組態檔的 **compilation**\/**assemblies** 區段底下。 下列範例為其示範。  
  
```  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [編譯組件的 add 項目 \(ASP.NET 設定結構描述\)](http://msdn.microsoft.com/zh-tw/602197e8-108d-4249-b752-ba2a318f75e4)。  
  
## 請參閱  
 [ASP.NET Trust Levels and Policy Files](../Topic/ASP.NET%20Trust%20Levels%20and%20Policy%20Files.md)   
 [securityPolicy 項目 \(ASP.NET 設定結構描述\)](http://msdn.microsoft.com/zh-tw/469d8d22-d263-46bb-8400-40d8d027faba)   
 [交易管理擴大規模案例 ](../../../../docs/framework/data/transactions/transaction-management-escalation.md)