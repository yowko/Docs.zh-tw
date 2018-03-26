---
title: 根據開發情況比較 ASP.NET Web 服務與 WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c12bd11cee62cd769f7dffc142806fa5ab1b0137
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="57e76-102">根據開發情況比較 ASP.NET Web 服務與 WCF</span><span class="sxs-lookup"><span data-stu-id="57e76-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="57e76-103"> 具有 ASP.NET 相容性模式選項，可讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式以類似 ASP.NET Web 服務的方式來進行程式設計和組態，並且可模擬其行為。</span><span class="sxs-lookup"><span data-stu-id="57e76-103"> has an ASP.NET compatibility mode option to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="57e76-104">下列章節將根據使用這兩種技術來開發應用程式時的需求，比較 ASP.NET Web 服務和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="57e76-104">The following sections compare ASP.NET Web services and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] based on what is required to develop applications using both technologies.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="57e76-105">資料表示</span><span class="sxs-lookup"><span data-stu-id="57e76-105">Data Representation</span></span>  
 <span data-ttu-id="57e76-106">使用 ASP.NET 開發 Web 服務時，通常一開始會先定義服務所要使用的任何複雜資料型別。</span><span class="sxs-lookup"><span data-stu-id="57e76-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="57e76-107">ASP.NET 會依賴 <xref:System.Xml.Serialization.XmlSerializer> 將 .NET Framework 型別表示的資料轉譯為 XML 以便與服務進行來回傳輸，以及將接收到的 XML 資料轉譯為 .NET Framework 物件。</span><span class="sxs-lookup"><span data-stu-id="57e76-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="57e76-108">定義 ASP.NET 服務所要使用的複雜資料型別時需要定義 .NET Framework 類別，這個類別可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化成 XML 以及從 XML 還原序列化。</span><span class="sxs-lookup"><span data-stu-id="57e76-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="57e76-109">這種類別可手動撰寫，或是使用命令列 XML 結構描述/資料型別支援公用程式 xsd.exe，從 XML 結構描述中的型別定義產生。</span><span class="sxs-lookup"><span data-stu-id="57e76-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>  
  
 <span data-ttu-id="57e76-110">下列清單列出在定義可由 <xref:System.Xml.Serialization.XmlSerializer> 序列化成 XML 以及從 XML 還原序列化的 .NET Framework 類別時，必須瞭解的主要問題：</span><span class="sxs-lookup"><span data-stu-id="57e76-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>  
  
-   <span data-ttu-id="57e76-111">只有 .NET Framework 物件的公用欄位和屬性會轉譯為 XML。</span><span class="sxs-lookup"><span data-stu-id="57e76-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>  
  
-   <span data-ttu-id="57e76-112">集合類別 (Collection Class) 的執行個體只有在類別實作 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.ICollection> 介面時，才能序列化為 XML。</span><span class="sxs-lookup"><span data-stu-id="57e76-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>  
  
-   <span data-ttu-id="57e76-113">實作 <xref:System.Collections.IDictionary> 介面的類別 (例如 <xref:System.Collections.Hashtable>) 並不能序列化為 XML。</span><span class="sxs-lookup"><span data-stu-id="57e76-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>  
  
-   <span data-ttu-id="57e76-114">絕大多數在 <xref:System.Xml.Serialization> 命名空間 (Namespace) 中的屬性型別可以新增至 .NET Framework 類別及其成員，以控制如何使用 XML 來表示此類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="57e76-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57e76-115"> 應用程式的開發通常也是從定義複雜類型開始。</span><span class="sxs-lookup"><span data-stu-id="57e76-115"> application development usually also begins with the definition of complex types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57e76-116"> 可以設定為使用與 ASP.NET Web 服務相同的 .NET Framework 型別。</span><span class="sxs-lookup"><span data-stu-id="57e76-116"> can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="57e76-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.Runtime.Serialization.DataContractAttribute>和<xref:System.Runtime.Serialization.DataMemberAttribute>可以加入表示類型的執行個體已序列化為 XML，以及哪些特定欄位或屬性的型別進行序列化，如下列範例所示的.NET Framework 型別程式碼。</span><span class="sxs-lookup"><span data-stu-id="57e76-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>  
  
```  
//Example One:   
[DataContract]  
public class LineItem  
{  
    [DataMember]  
    public string ItemNumber;  
    [DataMember]  
    public decimal Quantity;  
    [DataMember]  
    public decimal UnitPrice;  
}  
  
//Example Two:   
public class LineItem  
{  
    [DataMember]  
    private string itemNumber;  
    [DataMember]  
    private decimal quantity;  
    [DataMember]  
    private decimal unitPrice;  
  
    public string ItemNumber  
    {  
      get  
      {  
          return this.itemNumber;  
      }  
  
      set  
      {  
          this.itemNumber = value;  
      }  
    }  
  
    public decimal Quantity  
    {  
        get  
        {  
            return this.quantity;  
        }  
  
        set  
        {  
            this.quantity = value;  
        }  
    }  
  
    public decimal UnitPrice  
    {  
      get  
      {  
          return this.unitPrice;  
      }  
  
      set  
      {  
          this.unitPrice = value;  
      }  
    }  
}  
  
//Example Three:   
public class LineItem  
{  
     private string itemNumber;  
     private decimal quantity;  
     private decimal unitPrice;  
  
     [DataMember]  
     public string ItemNumber  
     {  
       get  
       {  
          return this.itemNumber;  
       }  
  
       set  
       {  
           this.itemNumber = value;  
       }  
     }  
  
     [DataMember]  
     public decimal Quantity  
     {  
          get  
          {  
              return this.quantity;  
          }  
  
          set  
          {  
             this.quantity = value;  
          }  
     }  
  
     [DataMember]  
     public decimal UnitPrice  
     {  
          get  
          {  
              return this.unitPrice;  
          }  
  
          set  
          {  
              this.unitPrice = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="57e76-118"><xref:System.Runtime.Serialization.DataContractAttribute> 表示要序列化型別的零或多個欄位或屬性，而 <xref:System.Runtime.Serialization.DataMemberAttribute> 則表示會序列化特定的欄位或屬性。</span><span class="sxs-lookup"><span data-stu-id="57e76-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="57e76-119"><xref:System.Runtime.Serialization.DataContractAttribute> 可以套用於類別或結構。</span><span class="sxs-lookup"><span data-stu-id="57e76-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="57e76-120"><xref:System.Runtime.Serialization.DataMemberAttribute> 可以套用至欄位或屬性 (Property)，而套用此屬性 (Attribute) 的欄位和屬性 (Property) 可以是公用或私用。</span><span class="sxs-lookup"><span data-stu-id="57e76-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="57e76-121">在 <xref:System.Runtime.Serialization.DataContractAttribute> 中，已套用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 之型別的執行個體是指資料合約。</span><span class="sxs-lookup"><span data-stu-id="57e76-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="57e76-122">這些資料合約會使用 <xref:System.Runtime.Serialization.DataContractSerializer> 來序列化為 XML。</span><span class="sxs-lookup"><span data-stu-id="57e76-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="57e76-123">下列為使用 <xref:System.Runtime.Serialization.DataContractSerializer> 和使用 <xref:System.Xml.Serialization.XmlSerializer> 之間的重要差異清單，以及 <xref:System.Xml.Serialization> 命名空間的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="57e76-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>  
  
-   <span data-ttu-id="57e76-124"><xref:System.Xml.Serialization.XmlSerializer> 和 <xref:System.Xml.Serialization> 命名空間屬性是設計用來讓您將 .NET Framework 型別對應至 XML 結構描述中任何有效型別，因此，它們會就控制如何使用 XML 來表示型別方面提供極為精密的控制。</span><span class="sxs-lookup"><span data-stu-id="57e76-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="57e76-125"><xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 對於控制如何使用 XML 來表示型別則提供較少的控制。</span><span class="sxs-lookup"><span data-stu-id="57e76-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="57e76-126">您只能指定在採用 XML 時用來表示型別及其欄位或屬性的命名空間和名稱，以及指定這些欄位和屬性在 XML 中的顯示順序：</span><span class="sxs-lookup"><span data-stu-id="57e76-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>  
  
    ```  
    [DataContract(  
    Namespace="urn:Contoso:2006:January:29",  
    Name="LineItem")]  
    public class LineItem  
    {  
         [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]  
         public string itemNumber;  
         [DataMember(Name="Quantity",IsRequired=false,Order = 1)]  
         public decimal quantity;  
         [DataMember(Name="Price",IsRequired=false,Order = 2)]  
         public decimal unitPrice;  
    }  
    ```  
  
     <span data-ttu-id="57e76-127">有關用來表示 .NET 型別之 XML 結構的其他任何項目，都由 <xref:System.Runtime.Serialization.DataContractSerializer> 決定。</span><span class="sxs-lookup"><span data-stu-id="57e76-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
-   <span data-ttu-id="57e76-128">透過這樣對如何使用 XML 來表示型別不允許太多控制的方式，使得 <xref:System.Runtime.Serialization.DataContractSerializer> 非常易於預測序列化 (Serialization) 處理序 (Process)，也因此更容易進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="57e76-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="57e76-129"><xref:System.Runtime.Serialization.DataContractSerializer> 設計的實質優點是提供更高的效能 (約提升 10% 的效能)。</span><span class="sxs-lookup"><span data-stu-id="57e76-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>  
  
-   <span data-ttu-id="57e76-130">搭配 <xref:System.Xml.Serialization.XmlSerializer> 使用的屬性並不會指出要將型別的哪些欄位或屬性序列化為 XML，不過搭配 <xref:System.Runtime.Serialization.DataMemberAttribute> 使用的 <xref:System.Runtime.Serialization.DataContractSerializer> 會明確指示哪些欄位或屬性會進行序列化。</span><span class="sxs-lookup"><span data-stu-id="57e76-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="57e76-131">因此，資料合約為應用程式所要傳送及接收之資料結構的明確合約。</span><span class="sxs-lookup"><span data-stu-id="57e76-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>  
  
-   <span data-ttu-id="57e76-132"><xref:System.Xml.Serialization.XmlSerializer> 只能將 .NET 物件的 Public 成員轉譯為 XML，而 <xref:System.Runtime.Serialization.DataContractSerializer> 則不論這些物件成員的存取修飾詞為何都會將這些成員轉譯為 XML。</span><span class="sxs-lookup"><span data-stu-id="57e76-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>  
  
-   <span data-ttu-id="57e76-133">這樣會導致其能夠將型別的非 Public 成員序列化為 XML，進而使得 <xref:System.Runtime.Serialization.DataContractSerializer> 在可以處理序列化為 XML 的各種 .NET 型別上具有較少限制。</span><span class="sxs-lookup"><span data-stu-id="57e76-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="57e76-134">特別值得一提的是，它可以將像是實作 <xref:System.Collections.Hashtable> 介面的 <xref:System.Collections.IDictionary> 的型別轉譯為 XML 型別。</span><span class="sxs-lookup"><span data-stu-id="57e76-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="57e76-135"><xref:System.Runtime.Serialization.DataContractSerializer> 很有可能可以在不用修改型別定義或為型別開發包裝函式的情況下，將任何預先存在的 .NET 型別執行個體轉譯為 XML。</span><span class="sxs-lookup"><span data-stu-id="57e76-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>  
  
-   <span data-ttu-id="57e76-136">對於 <xref:System.Runtime.Serialization.DataContractSerializer> 來說，能夠存取型別的非 Public 成員能力會造成它需要完全信任，而 <xref:System.Xml.Serialization.XmlSerializer> 則不需要。</span><span class="sxs-lookup"><span data-stu-id="57e76-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="57e76-137">對於可透過用於執行此程式碼之認證來存取的電腦上所有資源，完全信任程式碼存取權限會提供這些資源的完整存取權。</span><span class="sxs-lookup"><span data-stu-id="57e76-137">The Full Trust code access permission give complete access to all resources on a machine that can be access using the credentials under which the code is executing.</span></span> <span data-ttu-id="57e76-138">由於完全信任的程式碼會存取電腦上的所有資源，所以請務必小心使用此選項。</span><span class="sxs-lookup"><span data-stu-id="57e76-138">This options should be used with care as fully trusted code accesses all resources on your machine.</span></span>  
  
-   <span data-ttu-id="57e76-139"><xref:System.Runtime.Serialization.DataContractSerializer> 併入了一些版本控制功能的支援：</span><span class="sxs-lookup"><span data-stu-id="57e76-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>  
  
    -   <span data-ttu-id="57e76-140"><xref:System.Runtime.Serialization.DataMemberAttribute> 具有 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性，這個屬性可以指派 false 的值以表示新增到資料合約新版本的成員 (沒有出現在舊版本中)，這樣便可以讓擁有新版合約的應用程式可以處理舊版合約。</span><span class="sxs-lookup"><span data-stu-id="57e76-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>  
  
    -   <span data-ttu-id="57e76-141">藉由讓資料合約實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面，便可讓 <xref:System.Runtime.Serialization.DataContractSerializer> 將定義於新版資料合約中的成員透過擁有舊版合約的應用程式傳遞。</span><span class="sxs-lookup"><span data-stu-id="57e76-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>  
  
 <span data-ttu-id="57e76-142">儘管存在以上這些差異，但根據預設，只要 XML 的命名空間已明確定義，<xref:System.Xml.Serialization.XmlSerializer> 序列化型別的目標 XML 與 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化型別的目標 XML 在語意上是完全相同的。</span><span class="sxs-lookup"><span data-stu-id="57e76-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="57e76-143">下列擁有可搭配這兩種序列化程式使用之屬性的類別，會由 <xref:System.Xml.Serialization.XmlSerializer> 和 <xref:System.Runtime.Serialization.DataContractAttribute> 轉譯為相同語意的 XML：</span><span class="sxs-lookup"><span data-stu-id="57e76-143">The following class, which has attributes for use with both of the serializers, are translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>  
  
```  
[Serializable]  
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]  
[DataContract(Namespace="urn:Contoso:2006:January:29")]  
public class LineItem  
{  
     [DataMember]  
     public string ItemNumber;  
     [DataMember]  
     public decimal Quantity;  
     [DataMember]  
     public decimal UnitPrice;  
}  
```  
  
 <span data-ttu-id="57e76-144">Windows 軟體開發套件 (SDK) 包含一個命令列工具，稱為[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。要與 ASP.NET Web 服務所使用的 xsd.exe 工具 Svcutil.exe 可從 XML 結構描述產生的.NET 資料型別定義。</span><span class="sxs-lookup"><span data-stu-id="57e76-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="57e76-145">如果 <xref:System.Runtime.Serialization.DataContractSerializer> 可以發出採用 XML 結構描述定義格式的 XML，型別就是資料合約，否則這些型別會使用 <xref:System.Xml.Serialization.XmlSerializer> 來進行序列化。</span><span class="sxs-lookup"><span data-stu-id="57e76-145">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="57e76-146">此工具 Svcutil.exe 工具也可以設定為使用其 `/dataContractOnly` 參數，從資料合約產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="57e76-146">The tool, Svcutil.exe, can also be made to generate XML Schema from data contracts using its `/dataContractOnly` switch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57e76-147">雖然 ASP.NET Web 服務使用 <xref:System.Xml.Serialization.XmlSerializer>，而且 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET 相容性模式會讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務模擬 ASP.NET Web 服務的行為，但 ASP.NET 相容性模式選項並不會限制要求使用 <xref:System.Xml.Serialization.XmlSerializer>。</span><span class="sxs-lookup"><span data-stu-id="57e76-147">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode makes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="57e76-148">使用者還是可以搭配 ASP.NET 相容性模式中的執行服務使用 <xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="57e76-148">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="57e76-149">服務開發</span><span class="sxs-lookup"><span data-stu-id="57e76-149">Service Development</span></span>  
 <span data-ttu-id="57e76-150">若要使用 ASP.NET 開發服務，習慣上會將 <xref:System.Web.Services.WebService> 屬性新增至類別，以及將 <xref:System.Web.Services.WebMethodAttribute> 新增至該類別要成為服務作業的任何方法：</span><span class="sxs-lookup"><span data-stu-id="57e76-150">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>  
  
```  
[WebService]  
public class Service : T:System.Web.Services.WebService  
{  
    [WebMethod]  
    public string Echo(string input)   
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="57e76-151">ASP.NET 2.0 引入了將屬性 <xref:System.Web.Services.WebService> 和 <xref:System.Web.Services.WebMethodAttribute> 新增至介面 (而非類別)，以及撰寫類別來實作介面的選項：</span><span class="sxs-lookup"><span data-stu-id="57e76-151">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>  
  
```  
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="57e76-152">我們建議您使用這個選項，因為具有 <xref:System.Web.Services.WebService> 屬性的介面會構成可以讓不同類別重複使用之服務所執行的作業合約，而這些類別可能會用不同方式來實作該份相同合約。</span><span class="sxs-lookup"><span data-stu-id="57e76-152">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="57e76-153">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的提供方式為定義一個或多個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 端點。</span><span class="sxs-lookup"><span data-stu-id="57e76-153">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is provided by defining one or more [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints.</span></span> <span data-ttu-id="57e76-154">端點會由位址、繫結和服務合約所定義。</span><span class="sxs-lookup"><span data-stu-id="57e76-154">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="57e76-155">位址會定義服務的所在位置。</span><span class="sxs-lookup"><span data-stu-id="57e76-155">The address defines where the service is located.</span></span> <span data-ttu-id="57e76-156">繫結會指定與服務的通訊方式。</span><span class="sxs-lookup"><span data-stu-id="57e76-156">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="57e76-157">服務合約會定義服務可以執行的作業。</span><span class="sxs-lookup"><span data-stu-id="57e76-157">The service contract defines the operations that the service can perform.</span></span>  
  
 <span data-ttu-id="57e76-158">通常會先定義服務合約，定義方式是將 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 新增至介面：</span><span class="sxs-lookup"><span data-stu-id="57e76-158">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <span data-ttu-id="57e76-159"><xref:System.ServiceModel.ServiceContractAttribute> 會指示該介面會定義 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務合約，而 <xref:System.ServiceModel.OperationContractAttribute> 則表示介面中的哪一個方法 (如果有的話) 要定義服務合約的作業。</span><span class="sxs-lookup"><span data-stu-id="57e76-159">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>  
  
 <span data-ttu-id="57e76-160">完成定義服務合約之後，這個服務合約就會在類別實作用來定義此服務合約之介面的程序下，實作於類別中：</span><span class="sxs-lookup"><span data-stu-id="57e76-160">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="57e76-161">實作服務合約的類別在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中是指服務類型。</span><span class="sxs-lookup"><span data-stu-id="57e76-161">A class that implements a service contract is referred to as a service type in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="57e76-162">下一步是讓位址和繫結與服務類型產生關聯。</span><span class="sxs-lookup"><span data-stu-id="57e76-162">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="57e76-163">這項工作通常會在組態檔中完成，方法可以是直接編輯組態檔或使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所提供的組態編輯器。</span><span class="sxs-lookup"><span data-stu-id="57e76-163">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="57e76-164">下列是組態檔的範例。</span><span class="sxs-lookup"><span data-stu-id="57e76-164">Here is an example of a configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
     <system.serviceModel>  
      <services>  
      <service name="Service ">  
       <endpoint   
        address="EchoService"  
        binding="basicHttpBinding"  
        contract="IEchoService "/>  
      </service>  
      </services>  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="57e76-165">繫結會指定用來與應用程式通訊的一組通訊協定。</span><span class="sxs-lookup"><span data-stu-id="57e76-165">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="57e76-166">下表會列出表示常用選項的系統提供繫結。</span><span class="sxs-lookup"><span data-stu-id="57e76-166">The following table lists the system-provided bindings that represent common options.</span></span>  
  
|<span data-ttu-id="57e76-167">名稱</span><span class="sxs-lookup"><span data-stu-id="57e76-167">Name</span></span>|<span data-ttu-id="57e76-168">用途</span><span class="sxs-lookup"><span data-stu-id="57e76-168">Purpose</span></span>|  
|----------|-------------|  
|<span data-ttu-id="57e76-169">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="57e76-169">BasicHttpBinding</span></span>|<span data-ttu-id="57e76-170">與支援 WS-BasicProfile 1.1 和 Basic Security Profile 1.0 之 Web 服務和用戶端的互通性。</span><span class="sxs-lookup"><span data-stu-id="57e76-170">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|  
|<span data-ttu-id="57e76-171">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="57e76-171">WSHttpBinding</span></span>|<span data-ttu-id="57e76-172">與支援 WS-\* 通訊協定 (透過 HTTP) 之 Web 服務和用戶端的互通性。</span><span class="sxs-lookup"><span data-stu-id="57e76-172">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|  
|<span data-ttu-id="57e76-173">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="57e76-173">WSDualHttpBinding</span></span>|<span data-ttu-id="57e76-174">雙工 HTTP 通訊，使用這種通訊時，初始訊息的接收者不會直接回覆給初始傳送者，而是可能在一段期間使用符合 WS-\* 通訊協定的 HTTP 傳輸任意數目的回應。</span><span class="sxs-lookup"><span data-stu-id="57e76-174">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|  
|<span data-ttu-id="57e76-175">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="57e76-175">WSFederationBinding</span></span>|<span data-ttu-id="57e76-176">HTTP 通訊，其中可以根據明確識別之認證提供者所發行的認證來控制對服務資源的存取。</span><span class="sxs-lookup"><span data-stu-id="57e76-176">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|  
|<span data-ttu-id="57e76-177">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="57e76-177">NetTcpBinding</span></span>|<span data-ttu-id="57e76-178">在整個網路之 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 軟體實體之間進行的安全、可靠、高效能通訊。</span><span class="sxs-lookup"><span data-stu-id="57e76-178">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities across a network.</span></span>|  
|<span data-ttu-id="57e76-179">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="57e76-179">NetNamedPipeBinding</span></span>|<span data-ttu-id="57e76-180">在相同電腦上之 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 軟體實體之間進行的安全、可靠、高效能通訊。</span><span class="sxs-lookup"><span data-stu-id="57e76-180">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities on the same machine.</span></span>|  
|<span data-ttu-id="57e76-181">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="57e76-181">NetMsmqBinding</span></span>|<span data-ttu-id="57e76-182">透過 MSMQ 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 軟體實體之間進行的通訊。</span><span class="sxs-lookup"><span data-stu-id="57e76-182">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using MSMQ.</span></span>|  
|<span data-ttu-id="57e76-183">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="57e76-183">MsmqIntegrationBinding</span></span>|<span data-ttu-id="57e76-184">透過 MSMQ 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 軟體實體和其他軟體實體之間進行的通訊。</span><span class="sxs-lookup"><span data-stu-id="57e76-184">Communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entity and another software entity by using MSMQ.</span></span>|  
|<span data-ttu-id="57e76-185">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="57e76-185">NetPeerTcpBinding</span></span>|<span data-ttu-id="57e76-186">透過 Windows 對等網路在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 軟體實體之間進行的通訊。</span><span class="sxs-lookup"><span data-stu-id="57e76-186">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using Windows Peer-to-Peer Networking.</span></span>|  
  
 <span data-ttu-id="57e76-187">系統提供的繫結 <xref:System.ServiceModel.BasicHttpBinding> 併入了 ASP.NET Web 服務所支援的通訊協定集合。</span><span class="sxs-lookup"><span data-stu-id="57e76-187">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="57e76-188">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式的自訂繫結可輕鬆定義為繫結項目類別集合，而這些類別會由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用來實作個別的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="57e76-188">Custom bindings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are easily defined as collections of the binding element classes that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses to implement individual protocols.</span></span> <span data-ttu-id="57e76-189">還可以撰寫新的繫結項目來表示額外的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="57e76-189">New binding elements can be written to represent additional protocols.</span></span>  
  
 <span data-ttu-id="57e76-190">服務類型的內部行為可以透過使用一系列類別的屬性 (稱為行為) 來進行調整。</span><span class="sxs-lookup"><span data-stu-id="57e76-190">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="57e76-191">在下面範例中，<xref:System.ServiceModel.ServiceBehaviorAttribute> 類別是用來指定此服務類型要成為多執行緒。</span><span class="sxs-lookup"><span data-stu-id="57e76-191">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 <span data-ttu-id="57e76-192">有些像是 <xref:System.ServiceModel.ServiceBehaviorAttribute> 的行為是屬性。</span><span class="sxs-lookup"><span data-stu-id="57e76-192">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="57e76-193">而具有系統管理員可能要設定之屬性的其他行為，則可以在應用程式的組態中進行修改。</span><span class="sxs-lookup"><span data-stu-id="57e76-193">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>  
  
 <span data-ttu-id="57e76-194">在程式設計服務類型時，常見的使用方式會包括 <xref:System.ServiceModel.OperationContext> 類別。</span><span class="sxs-lookup"><span data-stu-id="57e76-194">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="57e76-195">它的靜態 <xref:System.ServiceModel.OperationContext.Current%2A> 屬性會提供有關其中執行作業之內容資訊的存取。</span><span class="sxs-lookup"><span data-stu-id="57e76-195">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="57e76-196"><xref:System.ServiceModel.OperationContext> 類似於 <xref:System.Web.HttpContext> 和 <xref:System.EnterpriseServices.ContextUtil> 類別兩者。</span><span class="sxs-lookup"><span data-stu-id="57e76-196"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="57e76-197">裝載</span><span class="sxs-lookup"><span data-stu-id="57e76-197">Hosting</span></span>  
 <span data-ttu-id="57e76-198">ASP.NET Web 服務會編譯為類別庫 (Class Library) 組件。</span><span class="sxs-lookup"><span data-stu-id="57e76-198">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="57e76-199">此時會提供稱為服務檔的檔案，該檔案擁有 .asmx 的副檔名，而且它所包含的 `@ WebService` 指示詞可識別其中包含服務程式碼的類別，以及可在其中找到該類別的組件。</span><span class="sxs-lookup"><span data-stu-id="57e76-199">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 <span data-ttu-id="57e76-200">此服務檔會複製到網際網路資訊服務 (IIS) 中的 ASP.NET 應用程式根目錄，而組件則會複製到應用程式根目錄的 \bin 子目錄。</span><span class="sxs-lookup"><span data-stu-id="57e76-200">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="57e76-201">接著，該應用程式可以透過應用程式根目錄中服務檔的統一資源定位器 (URL) 來存取。</span><span class="sxs-lookup"><span data-stu-id="57e76-201">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57e76-202"> 服務可隨時裝載於 IIS 5.1 或 6.0、提供做為 IIS 7.0 一部分的 Windows Process Activation Service (WAS)，以及任何的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="57e76-202"> services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="57e76-203">若要將服務裝載於 IIS 5.1 或 6.0 之中，此服務必須使用 HTTP 做為通訊傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="57e76-203">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>  
  
 <span data-ttu-id="57e76-204">若要將服務裝載於 IIS 5.1、6.0 或 WAS 之中，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="57e76-204">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>  
  
1.  <span data-ttu-id="57e76-205">將服務類型編譯為類別庫組件。</span><span class="sxs-lookup"><span data-stu-id="57e76-205">Compile the service type into a class library assembly.</span></span>  
  
2.  <span data-ttu-id="57e76-206">使用可識別服務類型的 `@ ServiceHost` 指示詞，建立含有 .svc 副檔名的服務檔：</span><span class="sxs-lookup"><span data-stu-id="57e76-206">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  <span data-ttu-id="57e76-207">將服務檔複製到虛擬目錄，然後將組件複製到虛擬目錄的 \bin 子目錄。</span><span class="sxs-lookup"><span data-stu-id="57e76-207">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>  
  
4.  <span data-ttu-id="57e76-208">將組態檔複製到虛擬目錄，然後將檔案重新命名為 Web.config。</span><span class="sxs-lookup"><span data-stu-id="57e76-208">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>  
  
 <span data-ttu-id="57e76-209">接著，該應用程式可以透過應用程式根目錄中服務檔的 URL 來存取。</span><span class="sxs-lookup"><span data-stu-id="57e76-209">The application is then accessible by using the URL of the service file in the application root.</span></span>  
  
 <span data-ttu-id="57e76-210">若要將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務裝載於 .NET 應用程式，請將此服務類型編譯到應用程式所參考的類別庫組件，並將應用程式程式設計成使用 <xref:System.ServiceModel.ServiceHost> 類別來裝載服務。</span><span class="sxs-lookup"><span data-stu-id="57e76-210">To host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="57e76-211">下列是所需要的基礎程式設計範例：</span><span class="sxs-lookup"><span data-stu-id="57e76-211">The following is an example of the basic programming required:</span></span>  
  
```  
string httpBaseAddress = "http://www.contoso.com:8000/";  
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";  
  
Uri httpBaseAddressUri = new Uri(httpBaseAddress);  
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);  
  
Uri[] baseAdresses = new Uri[] {   
 httpBaseAddressUri,  
 tcpBaseAddressUri};  
  
using(ServiceHost host = new ServiceHost(  
typeof(Service), //"Service" is the name of the service type baseAdresses))  
{  
     host.Open();  
  
     […] //Wait to receive messages  
     host.Close();  
}  
```  
  
 <span data-ttu-id="57e76-212">下列範例會示範如何在 <xref:System.ServiceModel.ServiceHost> 的建構中指定一個或多個傳輸通訊協定的位址。</span><span class="sxs-lookup"><span data-stu-id="57e76-212">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="57e76-213">這些位址指的是基底位址 (Base Address)。</span><span class="sxs-lookup"><span data-stu-id="57e76-213">These addresses are referred to as base addresses.</span></span>  
  
 <span data-ttu-id="57e76-214">針對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務任何端點所提供的位址會相對於端點主機的基底位址。</span><span class="sxs-lookup"><span data-stu-id="57e76-214">The address provided for any endpoint of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="57e76-215">主機的每個通訊傳輸通訊協定都可以擁有一個基底位址。</span><span class="sxs-lookup"><span data-stu-id="57e76-215">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="57e76-216">在上述組態檔的範例組態中，針對端點選取的 <xref:System.ServiceModel.BasicHttpBinding> 會以 HTTP 做為傳輸通訊協定，因此端點 `EchoService` 的位址會相對於主機的 HTTP 基底位址。</span><span class="sxs-lookup"><span data-stu-id="57e76-216">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="57e76-217">在上述範例中的主機，須的 HTTP 基底位址http://www.contoso.com:8000/。</span><span class="sxs-lookup"><span data-stu-id="57e76-217">In the case of the host in the preceding example, the HTTP base address is http://www.contoso.com:8000/.</span></span> <span data-ttu-id="57e76-218">對於裝載於 IIS 或 WAS 的服務，其基底位址是服務之服務檔的 URL。</span><span class="sxs-lookup"><span data-stu-id="57e76-218">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>  
  
 <span data-ttu-id="57e76-219">只有裝載於 IIS 或 WAS 的服務，以及設定使用 HTTP 做為唯一傳輸通訊協定的服務，可以設定為使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET 相容性模式選項。</span><span class="sxs-lookup"><span data-stu-id="57e76-219">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode option.</span></span> <span data-ttu-id="57e76-220">若要開啟該選項，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="57e76-220">Turning that option on requires the following steps.</span></span>  
  
1.  <span data-ttu-id="57e76-221">程式設計人員必須將 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 屬性新增至服務類型，並指定允許或需要 ASP.NET 相容性模式。</span><span class="sxs-lookup"><span data-stu-id="57e76-221">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>  
  
    ```  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  <span data-ttu-id="57e76-222">系統管理員必須將此應用程式設定成使用 ASP.NET 相容性模式。</span><span class="sxs-lookup"><span data-stu-id="57e76-222">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>  
  
    ```xml  
    <configuration>  
         <system.serviceModel>  
          <services>  
          […]  
          </services>  
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57e76-223"> 應用程式也可以設定其服務檔的副檔名要使用 .asmx，而不是使用 .svc。</span><span class="sxs-lookup"><span data-stu-id="57e76-223"> applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>  
  
    ```xml  
    <system.web>  
         <compilation>  
          <compilation debug="true">  
          <buildProviders>  
           <remove extension=".asmx"/>  
           <add extension=".asmx"   
            type="System.ServiceModel.ServiceBuildProvider,   
            Systemm.ServiceModel,   
            Version=3.0.0.0,   
            Culture=neutral,   
            PublicKeyToken=b77a5c561934e089" />  
          </buildProviders>  
          </compilation>  
         </compilation>  
    </system.web>  
    ```  
  
     <span data-ttu-id="57e76-224">在將服務修改成使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 時，此選項可讓您不用修改已設定為使用 .asmx 服務檔之 URL 的用戶端。</span><span class="sxs-lookup"><span data-stu-id="57e76-224">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="client-development"></a><span data-ttu-id="57e76-225">用戶端開發</span><span class="sxs-lookup"><span data-stu-id="57e76-225">Client Development</span></span>  
 <span data-ttu-id="57e76-226">ASP.NET Web 服務的用戶端是使用命令列工具 WSDL.exe 所產生的，這項工具會提供 .asmx 檔案的 URL 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="57e76-226">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="57e76-227">所提供的對應工具[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]是[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="57e76-227">The corresponding tool provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="57e76-228">它會產生程式碼模組，其中包含服務合約的定義以及 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別的定義。</span><span class="sxs-lookup"><span data-stu-id="57e76-228">It generates a code module with the definition of the service contract and the definition of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class.</span></span> <span data-ttu-id="57e76-229">它還會產生含有服務位址和繫結的組態檔。</span><span class="sxs-lookup"><span data-stu-id="57e76-229">It also generates a configuration file with the address and binding of the service.</span></span>  
  
 <span data-ttu-id="57e76-230">在程式設計遠端服務的用戶端時，通常建議根據非同步模式來進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="57e76-230">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="57e76-231">根據預設，WSDL.exe 工具所產生的程式碼永遠可供同步和非同步模式使用。</span><span class="sxs-lookup"><span data-stu-id="57e76-231">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="57e76-232">產生的程式碼[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)可以提供的其中一個模式。</span><span class="sxs-lookup"><span data-stu-id="57e76-232">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="57e76-233">根據預設，此程式碼會提供給同步模式使用。</span><span class="sxs-lookup"><span data-stu-id="57e76-233">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="57e76-234">如果是使用 `/async` 參數來執行工具，所產生的程式碼會提供給非同步模式使用。</span><span class="sxs-lookup"><span data-stu-id="57e76-234">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>  
  
 <span data-ttu-id="57e76-235">根據預設，ASP.NET 的 WSDL.exe 工具在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別中所產生的名稱，並不保證會與 Svcutil.exe 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別中所產生的的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="57e76-235">There is no guarantee that names in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="57e76-236">尤其是，在 Svcutil.exe 工具產生的程式碼中，必須使用 <xref:System.Xml.Serialization.XmlSerializer> 進行序列化的類別屬性名稱預設會被加上後置字元 Property，但是 WSDL.exe 工具就不是這種情形。</span><span class="sxs-lookup"><span data-stu-id="57e76-236">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>  
  
## <a name="message-representation"></a><span data-ttu-id="57e76-237">訊息表示</span><span class="sxs-lookup"><span data-stu-id="57e76-237">Message Representation</span></span>  
 <span data-ttu-id="57e76-238">您可以自訂 ASP.NET Web 服務所傳送及接收之 SOAP 訊息的標頭。</span><span class="sxs-lookup"><span data-stu-id="57e76-238">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="57e76-239">此時會從 <xref:System.Web.Services.Protocols.SoapHeader> 衍生類別來定義標頭的結構，接著，使用 <xref:System.Web.Services.Protocols.SoapHeaderAttribute> 來表示標頭是否存在。</span><span class="sxs-lookup"><span data-stu-id="57e76-239">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>  
  
```  
public class SomeProtocol : SoapHeader  
{  
     public long CurrentValue;  
     public long Total;  
}  
  
[WebService]  
public interface IEcho  
{  
     SomeProtocol ProtocolHeader  
     {  
      get;  
     set;  
     }  
  
     [WebMethod]  
     [SoapHeader("ProtocolHeader")]  
     string PlaceOrders(PurchaseOrderType order);  
}  
  
public class Service: WebService, IEcho  
{  
     private SomeProtocol protocolHeader;  
  
     public SomeProtocol ProtocolHeader  
     {  
         get  
         {  
              return this.protocolHeader;  
         }  
  
         set  
         {  
              this.protocolHeader = value;  
         }  
     }  
  
     string PlaceOrders(PurchaseOrderType order)  
     {  
         long currentValue = this.protocolHeader.CurrentValue;  
     }  
}  
```  
  
 <span data-ttu-id="57e76-240">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會提供屬性 <xref:System.ServiceModel.MessageContractAttribute>、<xref:System.ServiceModel.MessageHeaderAttribute> 和 <xref:System.ServiceModel.MessageBodyMemberAttribute> 來描述服務所傳送及接收之 SOAP 訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="57e76-240">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>  
  
```  
[DataContract]  
public class SomeProtocol  
{  
     [DataMember]  
     public long CurrentValue;  
     [DataMember]  
     public long Total;  
}  
  
[DataContract]  
public class Item  
{  
     [DataMember]  
     public string ItemNumber;  
     [DataMember]  
     public decimal Quantity;  
     [DataMember]  
     public decimal UnitPrice;  
}  
  
[MessageContract]  
public class ItemMesage  
{  
     [MessageHeader]  
     public SomeProtocol ProtocolHeader;  
     [MessageBody]  
     public Item Content;  
}  
  
[ServiceContract]  
public interface IItemService  
{  
     [OperationContract]  
     public void DeliverItem(ItemMessage itemMessage);  
}  
```  
  
 <span data-ttu-id="57e76-241">這個語法會產生訊息結構的明確表示，而訊息的結構會隱含在 ASP.NET Web 服務的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="57e76-241">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="57e76-242">此外，使用 ASP.NET 語法時，訊息標頭會表示為服務的屬性，例如在先前範例中的 `ProtocolHeader` 屬性，若是使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 語法，訊息標頭就會更精確地表示為訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="57e76-242">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="57e76-243">此外，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 允許將訊息標頭新增至端點的組態中。</span><span class="sxs-lookup"><span data-stu-id="57e76-243">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows message headers to be added to the configuration of endpoints.</span></span>  
  
```xml  
<service name="Service ">  
     <endpoint   
      address="EchoService"  
      binding="basicHttpBinding"  
      contract="IEchoService ">  
      <headers>  
      <dsig:X509Certificate   
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">  
       ...  
      </dsig:X509Certificate>  
      </headers>  
     </endpoint>  
</service>  
```  
  
 <span data-ttu-id="57e76-244">該選項可讓您避免在用戶端或服務之程式碼中使用基礎結構通訊協定標頭的參考，實際上，這些標頭會依據端點的設定方式新增至訊息中。</span><span class="sxs-lookup"><span data-stu-id="57e76-244">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>  
  
## <a name="service-description"></a><span data-ttu-id="57e76-245">服務描述</span><span class="sxs-lookup"><span data-stu-id="57e76-245">Service Description</span></span>  
 <span data-ttu-id="57e76-246">使用查詢 WSDL 向 ASP.NET Web 服務 .asmx 檔案發出 HTTP GET 要求，會讓 ASP.NET 產生 WSDL 來描述服務。</span><span class="sxs-lookup"><span data-stu-id="57e76-246">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="57e76-247">它會傳回 WSDL 做為要求的回應。</span><span class="sxs-lookup"><span data-stu-id="57e76-247">It returns that WSDL as the response to the request.</span></span>  
  
 <span data-ttu-id="57e76-248">ASP.NET 2.0 可以驗證服務是否相容於 Web Services-Interoperability Organization (WS-I) 的 Basic Profile 1.1，而且可以插入有關服務相容於其 WSDL 的宣告。</span><span class="sxs-lookup"><span data-stu-id="57e76-248">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="57e76-249">透過 `ConformsTo` 屬性的 `EmitConformanceClaims` 和 <xref:System.Web.Services.WebServiceBindingAttribute> 參數，便可完成這個動作。</span><span class="sxs-lookup"><span data-stu-id="57e76-249">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="57e76-250">您可以自訂 ASP.NET 為服務產生的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="57e76-250">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="57e76-251">建立 <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> 的衍生類別來將項目新增至 WSDL，便可進行自訂。</span><span class="sxs-lookup"><span data-stu-id="57e76-251">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>  
  
 <span data-ttu-id="57e76-252">使用查詢 WSDL 向 IIS 51、6.0 或 WAS 所裝載之 HTTP 端點的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 .svc 檔案發出 HTTP GET 要求，會讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用 WSDL 回應來描述服務。</span><span class="sxs-lookup"><span data-stu-id="57e76-252">Issuing an HTTP GET request with the query WSDL for the .svc file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to respond with WSDL to describe the service.</span></span> <span data-ttu-id="57e76-253">使用查詢 WSDL 向 .NET 應用程式所裝載之服務的 HTTP 基底位址發出 HTTP GET 要求，如果 httpGetEnabled 設定為 true，也會產生相同作用。</span><span class="sxs-lookup"><span data-stu-id="57e76-253">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>  
  
 <span data-ttu-id="57e76-254">不過，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也會以自己為描述服務而產生的 WSDL 來回應 WS-MetadataExchange 要求。</span><span class="sxs-lookup"><span data-stu-id="57e76-254">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="57e76-255">ASP.NET Web 服務並沒有 WS-MetadataExchange 要求的內建支援。</span><span class="sxs-lookup"><span data-stu-id="57e76-255">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>  
  
 <span data-ttu-id="57e76-256">您還可以廣泛地自訂 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所產生的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="57e76-256">The WSDL that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates can be extensively customized.</span></span> <span data-ttu-id="57e76-257"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> 類別提供了一些可以自訂 WSDL 的功能。</span><span class="sxs-lookup"><span data-stu-id="57e76-257">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="57e76-258">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也可以設定為不產生 WSDL，而改用位於指定 URL 的靜態 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="57e76-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DescriptionBehavior">  
     <metadataPublishing   
      enableMetadataExchange="true"   
      enableGetWsdl="true"   
      enableHelpPage="true"   
      metadataLocation=  
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>  
     </behavior>  
</behaviors>  
```  
  
## <a name="exception-handling"></a><span data-ttu-id="57e76-259">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="57e76-259">Exception Handling</span></span>  
 <span data-ttu-id="57e76-260">在 ASP.NET Web 服務中，未處理的例外狀況會以 SOAP 錯誤傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="57e76-260">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="57e76-261">您也可以明確擲回 <xref:System.Web.Services.Protocols.SoapException> 類別的執行個體，並對傳輸給用戶端的 SOAP 錯誤內容擁有更高的控制。</span><span class="sxs-lookup"><span data-stu-id="57e76-261">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>  
  
 <span data-ttu-id="57e76-262">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務中，未處理的例外狀況不會以 SOAP 錯誤傳回給用戶端，以免不小心透過例外狀況公開機密資訊。</span><span class="sxs-lookup"><span data-stu-id="57e76-262">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="57e76-263">此時會提供組態設定，指定將未處理的例外狀況傳回給用戶端以進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="57e76-263">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>  
  
 <span data-ttu-id="57e76-264">若要將 SOAP 錯誤傳回給用戶端，您可以使用資料合約類型做為泛型型別，並擲回此泛型型別的執行個體，<xref:System.ServiceModel.FaultException%601>。</span><span class="sxs-lookup"><span data-stu-id="57e76-264">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="57e76-265">您還可以新增 <xref:System.ServiceModel.FaultContractAttribute> 屬性至作業，以指定作業可能產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="57e76-265">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>  
  
```  
[DataContract]  
public class MathFault  
{   
     [DataMember]  
     public string operation;  
     [DataMember]  
     public string problemType;  
}  
  
[ServiceContract]  
public interface ICalculator  
{  
     [OperationContract]  
     [FaultContract(typeof(MathFault))]  
     int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="57e76-266">這樣做會使得可能的錯誤將以 WSDL 向服務通告，讓用戶端程式設計人員預測作業可能產生的錯誤，並撰寫適當的 catch 陳述式。</span><span class="sxs-lookup"><span data-stu-id="57e76-266">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>  
  
```  
try  
{  
     result = client.Divide(value1, value2);  
}  
catch (FaultException<MathFault> e)  
{  
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "  
  + e.Detail.operation   
  + ". Problem: "   
  + e.Detail.problemType);  
}  
```  
  
## <a name="state-management"></a><span data-ttu-id="57e76-267">狀態管理</span><span class="sxs-lookup"><span data-stu-id="57e76-267">State Management</span></span>  
 <span data-ttu-id="57e76-268">用來實作 ASP.NET Web 服務的類別可以從 <xref:System.Web.Services.WebService> 衍生。</span><span class="sxs-lookup"><span data-stu-id="57e76-268">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 <span data-ttu-id="57e76-269">在這種情況下，該類別可以程式設計成使用 <xref:System.Web.Services.WebService> 基底類別 (Base Class) 的 Context 屬性來存取 <xref:System.Web.HttpContext> 物件。</span><span class="sxs-lookup"><span data-stu-id="57e76-269">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="57e76-270"><xref:System.Web.HttpContext> 物件可以使用其 Application 屬性來更新及擷取應用程式狀態資訊，並使用其 Session 屬性來更新及擷取工作階段狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="57e76-270">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>  
  
 <span data-ttu-id="57e76-271">對於透過使用 <xref:System.Web.HttpContext> 的 Session 屬性所存取之工作階段狀態資訊得實際存取位置，ASP.NET 提供了相當程度的控制。</span><span class="sxs-lookup"><span data-stu-id="57e76-271">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="57e76-272">此項資訊可能是儲存在 Cookie、資料庫、目前伺服器的記憶體，或是指定伺服器的記憶體中。</span><span class="sxs-lookup"><span data-stu-id="57e76-272">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="57e76-273">您可在服務的組態檔中選擇儲存位置。</span><span class="sxs-lookup"><span data-stu-id="57e76-273">The choice is made in the service’s configuration file.</span></span>  
  
 <span data-ttu-id="57e76-274">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會提供可擴充物件來進行狀態管理。</span><span class="sxs-lookup"><span data-stu-id="57e76-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides extensible objects for state management.</span></span> <span data-ttu-id="57e76-275">可擴充物件是指實作 <xref:System.ServiceModel.IExtensibleObject%601> 的物件。</span><span class="sxs-lookup"><span data-stu-id="57e76-275">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="57e76-276">最重要的擴充物件為 <xref:System.ServiceModel.ServiceHostBase> 和 <xref:System.ServiceModel.InstanceContext>。</span><span class="sxs-lookup"><span data-stu-id="57e76-276">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="57e76-277">`ServiceHostBase` 可讓您維護相同主機上所有服務類型之所有執行個體可以存取的狀態，而 `InstanceContext` 則可讓您維護相同服務類型執行個體中執行之任何程式碼可以存取的狀態。</span><span class="sxs-lookup"><span data-stu-id="57e76-277">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>  
  
 <span data-ttu-id="57e76-278">下面範例中的服務類型 `TradingSystem` 具有 <xref:System.ServiceModel.ServiceBehaviorAttribute>，這個屬性指定所有來自相同 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端執行個體的呼叫都要傳送至相同的服務類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="57e76-278">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client instance are routed to the same instance of the service type.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 <span data-ttu-id="57e76-279">類別 `DealData` 會定義相同服務類型執行個體中執行之任何程式碼可以存取的狀態。</span><span class="sxs-lookup"><span data-stu-id="57e76-279">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 <span data-ttu-id="57e76-280">在實作服務合約其中一個作業的服務類型程式碼中，`DealData` 狀態物件會新增至目前服務類型執行個體的狀態中。</span><span class="sxs-lookup"><span data-stu-id="57e76-280">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 <span data-ttu-id="57e76-281">接著，該狀態物件可由實作服務合約之其他作業的程式碼進行擷取和修改。</span><span class="sxs-lookup"><span data-stu-id="57e76-281">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 <span data-ttu-id="57e76-282">相對於 ASP.NET 會控制 <xref:System.Web.HttpContext> 類別中狀態資訊的實際儲存位置，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (至少在初始版本中) 對於可擴充物件的儲存位置並不會提供任何控制。</span><span class="sxs-lookup"><span data-stu-id="57e76-282">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="57e76-283">這一點充分地解釋了為什麼要選擇 ASP.NET 相容性模式來用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="57e76-283">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="57e76-284">如果可設定狀態管理是必要的工作，這時選擇 ASP.NET 相容性模式可讓您以與 ASP.NET 完全相同的方式來使用 <xref:System.Web.HttpContext> 類別的功能，而且也可以設定使用 <xref:System.Web.HttpContext> 類別管理之狀態資訊的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="57e76-284">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>  
  
## <a name="security"></a><span data-ttu-id="57e76-285">安全性</span><span class="sxs-lookup"><span data-stu-id="57e76-285">Security</span></span>  
 <span data-ttu-id="57e76-286">用來保護 ASP.NET Web 服務的選項，就是用來保護任何 IIS 應用程式的選項。</span><span class="sxs-lookup"><span data-stu-id="57e76-286">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="57e76-287">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式不只可以裝載於 IIS，也可以裝載於任何的 .NET 可執行檔中，因此用來保護 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式的選項必須設定成獨立於 IIS 的機能。</span><span class="sxs-lookup"><span data-stu-id="57e76-287">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can be hosted not only within IIS but also within any .NET executable, the options for securing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="57e76-288">不過，提供 ASP.NET Web 服務使用的機能，也可提供在 ASP.NET 相容性模式中的執行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務使用。</span><span class="sxs-lookup"><span data-stu-id="57e76-288">However, the facilities provided for ASP.NET Web services are also available for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-authentication"></a><span data-ttu-id="57e76-289">安全性：驗證</span><span class="sxs-lookup"><span data-stu-id="57e76-289">Security: Authentication</span></span>  
 <span data-ttu-id="57e76-290">IIS 會提供可以用來控制存取應用程式的機能，而您可以從其中選取匿名存取或各種的驗證模式：Windows 驗證、摘要式驗證、基本驗證和 .NET Passport 驗證。</span><span class="sxs-lookup"><span data-stu-id="57e76-290">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="57e76-291">Windows 驗證選項可用來控制 ASP.NET Web 服務的存取。</span><span class="sxs-lookup"><span data-stu-id="57e76-291">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="57e76-292">不過，當 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式是裝載於 IIS 時，IIS 就必須設定成允許匿名存取應用程式，這樣才能透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 本身來管理驗證，因為在其他各種選項中，只有它會支援 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="57e76-292">However, when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="57e76-293">其他選項還包括使用者名稱權杖、X.509 憑證、SAML 權杖和 CardSpace 卡，但是您也可以定義自訂的驗證機制。</span><span class="sxs-lookup"><span data-stu-id="57e76-293">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>  
  
### <a name="security-impersonation"></a><span data-ttu-id="57e76-294">安全性：模擬</span><span class="sxs-lookup"><span data-stu-id="57e76-294">Security: Impersonation</span></span>  
 <span data-ttu-id="57e76-295">ASP.NET 提供了身分識別項目，透過此項目，ASP.NET Web 服務便可設定成模擬特定的使用者，或是目前要求所提供的任何使用者認證。</span><span class="sxs-lookup"><span data-stu-id="57e76-295">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="57e76-296">該項目可用來設定在 ASP.NET 相容性模式中執行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式內的模擬。</span><span class="sxs-lookup"><span data-stu-id="57e76-296">That element can be used to configure impersonation in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications running in ASP.NET compatibility mode.</span></span>  
  
 <span data-ttu-id="57e76-297">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 組態系統會提供自己的身分識別項目來指定要模擬的特定使用者。</span><span class="sxs-lookup"><span data-stu-id="57e76-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="57e76-298">此外，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端和伺服器可以獨立設定用於模擬。</span><span class="sxs-lookup"><span data-stu-id="57e76-298">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="57e76-299">用戶端可以設定為在傳輸要求時模擬目前使用者。</span><span class="sxs-lookup"><span data-stu-id="57e76-299">Clients can be configured to impersonate the current user when they transmit requests.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="57e76-300">服務作業可以設定為模擬目前要求所提供的任何使用者認證。</span><span class="sxs-lookup"><span data-stu-id="57e76-300">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="57e76-301">安全性：使用存取控制清單進行驗證</span><span class="sxs-lookup"><span data-stu-id="57e76-301">Security: Authorization using Access Control Lists</span></span>  
 <span data-ttu-id="57e76-302">存取控制清單 (ACL) 可用來限制對 .asmx 檔案的存取。</span><span class="sxs-lookup"><span data-stu-id="57e76-302">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="57e76-303">不過，除非是在 ASP.NET 相容性模式下，否則 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .svc 檔案上的 ACL 會被忽略。</span><span class="sxs-lookup"><span data-stu-id="57e76-303">However, ACLs on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .svc files are ignored except in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-role-based-authorization"></a><span data-ttu-id="57e76-304">安全性：以角色為基礎的授權</span><span class="sxs-lookup"><span data-stu-id="57e76-304">Security: Role-based Authorization</span></span>  
 <span data-ttu-id="57e76-305">IIS Windows 驗證選項可以搭配 ASP.NET 設定語言所提供的 authorization 項目一起使用，以便根據獲指派使用者的 Windows 群組，為 ASP.NET Web 服務進行以角色為基礎的驗證。</span><span class="sxs-lookup"><span data-stu-id="57e76-305">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="57e76-306">ASP.NET 2.0 引進了更一般性的以角色為基礎的驗證機制：角色提供者。</span><span class="sxs-lookup"><span data-stu-id="57e76-306">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>  
  
 <span data-ttu-id="57e76-307">角色提供者為類別，這些類別全部都會實作可查詢使用者所獲派角色的基本介面，而且每個角色提供者都知道如何從不同來源擷取該資訊。</span><span class="sxs-lookup"><span data-stu-id="57e76-307">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="57e76-308">ASP.NET 2.0 會提供可自 Microsoft SQL Server 資料庫中擷取角色指派的角色提供者，並提供另一個可自 Windows Server 2003 授權管理員擷取角色指派的角色提供者。</span><span class="sxs-lookup"><span data-stu-id="57e76-308">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>  
  
 <span data-ttu-id="57e76-309">角色提供者機制的使用實際上可以獨立於任何 .NET 應用程式 (包括 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式) 中的 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="57e76-309">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="57e76-310">下列 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式的組態範例會示範如何透過 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 的方式來選取使用 ASP.NET 角色提供者選項。</span><span class="sxs-lookup"><span data-stu-id="57e76-310">The following sample configuration for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
     <services>  
         <service name="Service.ResourceAccessServiceType"   
             behaviorConfiguration="ServiceBehavior">  
             <endpoint   
              address="ResourceAccessService"   
              binding="wsHttpBinding"   
              contract="Service.IResourceAccessContract"/>  
         </service>  
     </services>  
     <behaviors>  
       <behavior name="ServiceBehavior">  
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>  
      </behavior>  
     </behaviors>  
</system.serviceModel>  
```  
  
### <a name="security-claims-based-authorization"></a><span data-ttu-id="57e76-311">安全性：宣告架構的授權</span><span class="sxs-lookup"><span data-stu-id="57e76-311">Security: Claims-based Authorization</span></span>  
 <span data-ttu-id="57e76-312">最重要的一項 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 創新功能，就是全面支援以宣告為基礎之受保護資源的授權存取。</span><span class="sxs-lookup"><span data-stu-id="57e76-312">One of the most important innovations of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="57e76-313">宣告是由類型、權限和值組成。以駕照為例，</span><span class="sxs-lookup"><span data-stu-id="57e76-313">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="57e76-314">駕照會建立一組關於持有人的宣告，而其中一個宣告是持有人的生日。</span><span class="sxs-lookup"><span data-stu-id="57e76-314">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="57e76-315">該宣告的類型為生日，而宣告的值為駕駛人的出生日期。</span><span class="sxs-lookup"><span data-stu-id="57e76-315">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="57e76-316">宣告賦予持有人的權限會指定持有人可以如何使用宣告值。</span><span class="sxs-lookup"><span data-stu-id="57e76-316">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="57e76-317">例如，在宣告為駕駛人生日、權限為持有的案例中：駕駛人持有該生日，但無法更改這個日期。</span><span class="sxs-lookup"><span data-stu-id="57e76-317">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="57e76-318">宣告架構的授權也包含以角色為基礎的驗證，因為角色就是一種宣告類型。</span><span class="sxs-lookup"><span data-stu-id="57e76-318">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>  
  
 <span data-ttu-id="57e76-319">宣告架構的授權方式會藉由將一組宣告與作業的存取需求進行比較，並根據該比較的結果授與或拒絕作業存取，來完成其作業。</span><span class="sxs-lookup"><span data-stu-id="57e76-319">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="57e76-320">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，您可以指定要用來執行宣告架構授權的類別，指定方式同樣指派值給 `ServiceAuthorizationManager` 的 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 屬性。</span><span class="sxs-lookup"><span data-stu-id="57e76-320">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="57e76-321">用來執行宣告架構授權的類別必須是衍生自 <xref:System.ServiceModel.ServiceAuthorizationManager>，而它只需要覆寫 `AccessCheck()` 方法。</span><span class="sxs-lookup"><span data-stu-id="57e76-321">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57e76-322"> 會在每次叫用服務作業時呼叫該方法，並提供 <xref:System.ServiceModel.OperationContext> 物件，而此物件會在其 `ServiceSecurityContext.AuthorizationContext` 屬性中包含使用者的宣告。</span><span class="sxs-lookup"><span data-stu-id="57e76-322"> calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="57e76-323"> 會從使用者提供以進行驗證的任何安全性權杖，執行組合使用者相關宣告的工作，而不評估這些宣告是否足以進行指定的作業。</span><span class="sxs-lookup"><span data-stu-id="57e76-323"> does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>  
  
 <span data-ttu-id="57e76-324">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會自動組合任何類型之安全性權杖中的宣告是一項很重要的創新，因為它會使宣告架構授權的程式碼完全獨立於驗證機制。</span><span class="sxs-lookup"><span data-stu-id="57e76-324">That [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="57e76-325">相對地，使用 ACL 或 ASP.NET 中角色的授權方式，與 Windows 驗證有密切的關係。</span><span class="sxs-lookup"><span data-stu-id="57e76-325">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>  
  
### <a name="security-confidentiality"></a><span data-ttu-id="57e76-326">安全性：機密性</span><span class="sxs-lookup"><span data-stu-id="57e76-326">Security: Confidentiality</span></span>  
 <span data-ttu-id="57e76-327">透過將 IIS 中的應用程式設定成使用 Secure Hypertext Transfer Protocol (HTTPS)，可以確保使用 ASP.NET Web 服務交換之訊息在傳輸層的機密性。</span><span class="sxs-lookup"><span data-stu-id="57e76-327">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="57e76-328">裝載於 IIS 的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式也可以採取相同的設定。</span><span class="sxs-lookup"><span data-stu-id="57e76-328">The same can be done for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted within IIS.</span></span> <span data-ttu-id="57e76-329">不過，裝載於 IIS 外部的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式也可以設定成使用安全傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="57e76-329">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="57e76-330">更重要的是，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式還可以設定為使用 WS-Security 通訊協定來保護訊息在傳送之前的安全。</span><span class="sxs-lookup"><span data-stu-id="57e76-330">More important, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="57e76-331">使用 WS-Security 來保護只有訊息本文的方式，可以讓訊息機密地在媒介中傳輸，直到訊息到達最終目的地為止。</span><span class="sxs-lookup"><span data-stu-id="57e76-331">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>  
  
## <a name="globalization"></a><span data-ttu-id="57e76-332">全球化</span><span class="sxs-lookup"><span data-stu-id="57e76-332">Globalization</span></span>  
 <span data-ttu-id="57e76-333">ASP.NET 設定語言可讓您指定個別服務的文化特性。</span><span class="sxs-lookup"><span data-stu-id="57e76-333">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="57e76-334">除非是在 ASP.NET 相容性模式下，否則 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 並不支援此組態設定。</span><span class="sxs-lookup"><span data-stu-id="57e76-334">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="57e76-335">若要當地語系化未使用 ASP.NET 相容性模式的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，請將服務類型編譯為文化特性特定的組件，並為各個文化特性特定的組件設定個別的文化特性特定端點。</span><span class="sxs-lookup"><span data-stu-id="57e76-335">To localize a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e76-336">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57e76-336">See Also</span></span>  
 [<span data-ttu-id="57e76-337">根據用途與使用的標準來比較 ASP.NET Web 服務與 WCF</span><span class="sxs-lookup"><span data-stu-id="57e76-337">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
