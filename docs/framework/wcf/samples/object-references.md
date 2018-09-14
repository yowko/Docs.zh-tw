---
title: 物件參考
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 1aa8b1c9d135186dba9e4da75f0c7cb9297d8e5c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594788"
---
# <a name="object-references"></a><span data-ttu-id="a1035-102">物件參考</span><span class="sxs-lookup"><span data-stu-id="a1035-102">Object References</span></span>
<span data-ttu-id="a1035-103">這個範例會示範如何以傳址 (By Reference) 方式，在伺服器和用戶端之間傳遞物件。</span><span class="sxs-lookup"><span data-stu-id="a1035-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="a1035-104">範例會使用模擬*社交網路*。</span><span class="sxs-lookup"><span data-stu-id="a1035-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="a1035-105">社交網路由包含 friend 清單的 `Person` 類別 (Class) 組成，每個 friend 都是一個 `Person` 類別的執行個體 (Instance)，擁有各自的 friend 清單。</span><span class="sxs-lookup"><span data-stu-id="a1035-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="a1035-106">這樣可以建立物件圖形。</span><span class="sxs-lookup"><span data-stu-id="a1035-106">This creates a graph of objects.</span></span> <span data-ttu-id="a1035-107">此服務會公開 (Expose) 這些社交網站上的作業。</span><span class="sxs-lookup"><span data-stu-id="a1035-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="a1035-108">在這個範例中，服務是由網際網路資訊服務 (IIS) 所裝載，而用戶端是主控台應用程式 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="a1035-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1035-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="a1035-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="a1035-110">服務</span><span class="sxs-lookup"><span data-stu-id="a1035-110">Service</span></span>  
 <span data-ttu-id="a1035-111">`Person` 類別已套用 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性 (Attribute)，而且 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 欄位設定為 `true` 以便將其宣告為參考型別 (Reference Type)。</span><span class="sxs-lookup"><span data-stu-id="a1035-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="a1035-112">所有屬性 (Property) 都已經套用 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="a1035-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
```  
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 <span data-ttu-id="a1035-113">`GetPeopleInNetwork` 作業會採用 `Person` 型別的參數並傳回網路中的所有人員，也就是 `friends` 清單中的所有人員、friend 的 friend 等等，但不包含重複項目。</span><span class="sxs-lookup"><span data-stu-id="a1035-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="a1035-114">`GetMutualFriends` 作業則採用 `Person` 型別的參數，並傳回清單中所有在其 `friends` 清單中亦包含這個人員的 friend。</span><span class="sxs-lookup"><span data-stu-id="a1035-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
```  
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 <span data-ttu-id="a1035-115">`GetCommonFriends` 作業會採用型別為 `Person` 的清單。</span><span class="sxs-lookup"><span data-stu-id="a1035-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="a1035-116">此清單應該會有兩個 `Person` 物件。</span><span class="sxs-lookup"><span data-stu-id="a1035-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="a1035-117">此作業會傳回 `Person` 物件的清單，這些物件都位於輸入清單中兩個 `friends` 物件的 `Person` 清單內。</span><span class="sxs-lookup"><span data-stu-id="a1035-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
```  
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a><span data-ttu-id="a1035-118">用戶端</span><span class="sxs-lookup"><span data-stu-id="a1035-118">Client</span></span>  
 <span data-ttu-id="a1035-119">使用建立用戶端 proxy**加入服務參考**Visual Studio 功能。</span><span class="sxs-lookup"><span data-stu-id="a1035-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="a1035-120">然後建立包含五個 `Person` 物件的社交網路。</span><span class="sxs-lookup"><span data-stu-id="a1035-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="a1035-121">這個用戶端會呼叫服務中所有三個方法。</span><span class="sxs-lookup"><span data-stu-id="a1035-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a1035-122">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="a1035-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a1035-123">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a1035-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a1035-124">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="a1035-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a1035-125">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a1035-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a1035-126">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a1035-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a1035-127">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a1035-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a1035-128">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="a1035-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1035-129">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a1035-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="a1035-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1035-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [<span data-ttu-id="a1035-131">互通物件參考</span><span class="sxs-lookup"><span data-stu-id="a1035-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
