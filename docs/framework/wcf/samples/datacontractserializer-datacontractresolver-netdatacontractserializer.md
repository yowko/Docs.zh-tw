---
title: "使用 DataContractSerializer 及 DataContractResolver 提供 NetDataContractSerializer 的功能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 使用 DataContractSerializer 及 DataContractResolver 提供 NetDataContractSerializer 的功能
此範例示範如何搭配適當的 <xref:System.Runtime.Serialization.DataContractResolver> 使用 <xref:System.Runtime.Serialization.DataContractSerializer> 以提供與 <xref:System.Runtime.Serialization.NetDataContractSerializer> 相同的功能。此範例示範如何建立適當的 <xref:System.Runtime.Serialization.DataContractResolver>，以及如何將其加入至 <xref:System.Runtime.Serialization.DataContractSerializer>。  
  
## 範例詳細資料  
 <xref:System.Runtime.Serialization.NetDataContractSerializer> 與 <xref:System.Runtime.Serialization.DataContractSerializer> 有一項重要的差異：<xref:System.Runtime.Serialization.NetDataContractSerializer> 在已序列化的 XML 中包含 CLR 型別資訊，而 <xref:System.Runtime.Serialization.DataContractSerializer> 則否。因此，只有當序列化和還原序列化兩端共用相同的 CLR 型別時，才能使用 <xref:System.Runtime.Serialization.NetDataContractSerializer>。不過，建議您使用 <xref:System.Runtime.Serialization.DataContractSerializer>，因為其效能比 <xref:System.Runtime.Serialization.NetDataContractSerializer> 更好。您可以在 <xref:System.Runtime.Serialization.DataContractSerializer> 中變更已序列化的資訊，只要在其中加入 <xref:System.Runtime.Serialization.DataContractResolver> 即可。  
  
 此範例包含二個專案。第一個專案使用 <xref:System.Runtime.Serialization.NetDataContractSerializer> 來序列化物件。第二個專案搭配 <xref:System.Runtime.Serialization.DataContractResolver> 使用 <xref:System.Runtime.Serialization.DataContractSerializer>，以提供與第一個專案相同的功能。  
  
 下列程式碼範例示範名稱為 `MyDataContractResolver`，且已加入至 DCSwithDCR 專案之 <xref:System.Runtime.Serialization.DataContractSerializer> 中的自訂 <xref:System.Runtime.Serialization.DataContractResolver> 實作。  
  
```  
class MyDataContractResolver : DataContractResolver  
{  
    private XmlDictionary dictionary = new XmlDictionary();  
  
    public MyDataContractResolver()  
    {  
    }  
  
    // Used at deserialization  
    // Allows users to map xsi:type name to any Type   
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        if (type == null)  
        {  
            type = Type.GetType(typeName + ", " + typeNamespace);  
        }  
        return type;  
    }  
  
    // Used at serialization  
    // Maps any Type to a new xsi:type representation  
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);  
        if (typeName == null || typeNamespace == null)  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add(dataContractType.FullName);  
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);  
        }  
    }  
}  
  
```  
  
#### 若要使用這個範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 DCRSample.sln 方案檔案。  
  
2.  以滑鼠右鍵按一下方案檔案，然後選擇 \[**屬性**\]。  
  
3.  在 \[**方案屬性頁**\] 對話方塊之 \[**通用屬性**\] 底下的 \[**啟始專案**\] 中，選取 \[**多個啟始專案:**\]。  
  
4.  在 \[**DCSwithDCR**\] 專案旁邊，選取 \[**動作**\] 下拉式清單中的 \[**啟動**\]。  
  
5.  在 \[**NetDCS**\] 專案旁邊，選取 \[**動作**\] 下拉式清單中的 \[**啟動**\]。  
  
6.  按一下 \[**確定**\] 以關閉對話方塊。  
  
7.  若要建置此方案，請按下 CTRL\+SHIFT\+B。  
  
8.  若要執行此方案，請按下 CTRL\+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
## 請參閱