---
title: DataContractSerializer 範例
description: 這個範例會示範 WCF 中的 DataContractSerializer，它會執行資料合約類別的一般序列化和還原序列化服務。
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: d38dddcaff7316f4933207c4aa0897ad47306352
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253611"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="b9400-103">DataContractSerializer 範例</span><span class="sxs-lookup"><span data-stu-id="b9400-103">DataContractSerializer Sample</span></span>

<span data-ttu-id="b9400-104">DataContractSerializer 範例會示範執行資料合約類別之一般序列化與還原序列化服務的 <xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="b9400-104">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="b9400-105">此範例會建立 `Record` 物件、將它序列化為記憶體資料流程，並將記憶體資料流程還原序列化為另一個 `Record` 物件，以示範的使用方式 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="b9400-105">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="b9400-106">此範例會接著會序列化使用二進位寫入器的 `Record` 物件，以便示範該寫入器會如何影響序列化。</span><span class="sxs-lookup"><span data-stu-id="b9400-106">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9400-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="b9400-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b9400-108">下列範例程式碼示範 `Record` 的資料合約。</span><span class="sxs-lookup"><span data-stu-id="b9400-108">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```csharp  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return $"Record: {n1} {operation} {n2} = {result}";
    }  
}  
```  
  
 <span data-ttu-id="b9400-109">此段範例程式碼會建立名為 `Record` 的 `record1` 物件，並接著顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="b9400-109">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="b9400-110">此範例會接著使用 <xref:System.Runtime.Serialization.DataContractSerializer>，將 `record1` 序列化為記憶體資料流。</span><span class="sxs-lookup"><span data-stu-id="b9400-110">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="b9400-111">接下來，此範例會使用 <xref:System.Runtime.Serialization.DataContractSerializer>，將記憶體資料流還原序列化為新 `Record` 物件，並顯示該物件。</span><span class="sxs-lookup"><span data-stu-id="b9400-111">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="b9400-112">根據預設，`DataContractSerializer` 會將物件編碼為使用 XML 文字表示法的資料流。</span><span class="sxs-lookup"><span data-stu-id="b9400-112">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="b9400-113">但是，您可以傳遞不同的寫入器來決定 XML 編碼的方式。</span><span class="sxs-lookup"><span data-stu-id="b9400-113">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="b9400-114">此範例會透過呼叫 <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A> 來建立二進位寫入器。</span><span class="sxs-lookup"><span data-stu-id="b9400-114">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="b9400-115">接著此範例會在呼叫 <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A> 時，將寫入器與記錄物件傳遞至序列化程式。</span><span class="sxs-lookup"><span data-stu-id="b9400-115">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="b9400-116">最後，此範例會清除寫入器，並報告關於資料流長度的資訊。</span><span class="sxs-lookup"><span data-stu-id="b9400-116">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="b9400-117">當執行範例時，原始記錄與已還原序列化的記錄會顯示出來，之後會顯示文字編碼與二進位編碼長度之間的比較結果。</span><span class="sxs-lookup"><span data-stu-id="b9400-117">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="b9400-118">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="b9400-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b9400-119">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="b9400-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b9400-120">確定您已 [針對 Windows Communication Foundation 範例執行一次性安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b9400-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b9400-121">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="b9400-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b9400-122">若要執行範例，請從命令提示字元輸入 client\bin\client.exe 以啟動用戶端。</span><span class="sxs-lookup"><span data-stu-id="b9400-122">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b9400-123">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="b9400-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b9400-124">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="b9400-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b9400-125">如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="b9400-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b9400-126">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="b9400-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
