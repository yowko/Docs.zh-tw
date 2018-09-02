---
title: 使用自訂類型之切換活動的使用
ms.date: 03/30/2017
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
ms.openlocfilehash: b24a03573b31f3fb1c34d4aa6e03bc11f5b25455
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423561"
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a><span data-ttu-id="d748b-102">使用自訂類型之切換活動的使用</span><span class="sxs-lookup"><span data-stu-id="d748b-102">Usage of the Switch Activity with Custom Types</span></span>
<span data-ttu-id="d748b-103">這個範例描述如何啟用 <xref:System.Activities.Statements.Switch%601> 活動，在執行階段評估使用者定義的複雜類型。</span><span class="sxs-lookup"><span data-stu-id="d748b-103">This sample describes how to enable a <xref:System.Activities.Statements.Switch%601> activity to evaluate a user-defined complex type at runtime.</span></span> <span data-ttu-id="d748b-104">在大部分傳統的程序性程式設計語言，[切換](https://go.microsoft.com/fwlink/?LinkId=180521)陳述式選取根據變數的條件式評估的執行邏輯。</span><span class="sxs-lookup"><span data-stu-id="d748b-104">In most traditional procedural programming languages, a [switch](https://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable.</span></span> <span data-ttu-id="d748b-105">傳統上，`switch` 陳述式適用於可靜態評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="d748b-105">Traditionally, a `switch` statement operates on an expression that can be statically evaluated.</span></span> <span data-ttu-id="d748b-106">例如，在 C# 中，這表示僅支援基本型別 (例如 <xref:System.Boolean>、<xref:System.Int32> 和 <xref:System.String>)，以及列舉型別。</span><span class="sxs-lookup"><span data-stu-id="d748b-106">For example, in C# this means that only primitive types, such as <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, and enumeration types are supported.</span></span>  
  
 <span data-ttu-id="d748b-107">若要在自訂類別上啟用切換，必須實作可在執行階段評估自訂複雜類型值的邏輯。</span><span class="sxs-lookup"><span data-stu-id="d748b-107">To enable switching on a custom class, logic must be implemented to evaluate values of the custom complex type at runtime.</span></span> <span data-ttu-id="d748b-108">這個範例示範如何在名為 `Person` 的自訂複雜類型上啟用切換。</span><span class="sxs-lookup"><span data-stu-id="d748b-108">This sample demonstrates how to enable switching on a custom complex type named `Person`.</span></span>  
  
-   <span data-ttu-id="d748b-109">在自訂類別 `Person` 中，<xref:System.ComponentModel.TypeConverter> 屬性是以自訂 <xref:System.ComponentModel.TypeConverter> 的名稱來宣告。</span><span class="sxs-lookup"><span data-stu-id="d748b-109">In the custom class `Person`, a <xref:System.ComponentModel.TypeConverter> attribute is declared with the name of the custom <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   <span data-ttu-id="d748b-110">在自訂類別 `Person` 中，會覆寫 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 類別。</span><span class="sxs-lookup"><span data-stu-id="d748b-110">In the custom class `Person`, the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> classes are overridden.</span></span>  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
    ```  
  
-   <span data-ttu-id="d748b-111">實作自訂 <xref:System.ComponentModel.TypeConverter> 類別，將自訂類別執行個體轉換成字串，並將字串轉換成自訂類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="d748b-111">A custom <xref:System.ComponentModel.TypeConverter> class is implemented that performs the conversion of an instance of the custom class to a string and a string to an instance of a custom class.</span></span>  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 <span data-ttu-id="d748b-112">下列檔案包含在此範例中：</span><span class="sxs-lookup"><span data-stu-id="d748b-112">The following files are included in this sample:</span></span>  
  
-   <span data-ttu-id="d748b-113">**Person.cs**： 定義`Person`類別。</span><span class="sxs-lookup"><span data-stu-id="d748b-113">**Person.cs**: Defines the `Person` class.</span></span>  
  
-   <span data-ttu-id="d748b-114">**PersonConverter.cs**： 的類型轉換器`Person`類別。</span><span class="sxs-lookup"><span data-stu-id="d748b-114">**PersonConverter.cs**: The type converter for the `Person` class.</span></span>  
  
-   <span data-ttu-id="d748b-115">**Sequence.xaml**： 切換工作流程`Person`型別。</span><span class="sxs-lookup"><span data-stu-id="d748b-115">**Sequence.xaml**: a workflow that switches over the `Person` type.</span></span>  
  
-   <span data-ttu-id="d748b-116">**Program.cs**: main 函式執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="d748b-116">**Program.cs**: The main function that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d748b-117">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="d748b-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="d748b-118">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入 Switch.sln。</span><span class="sxs-lookup"><span data-stu-id="d748b-118">Load Switch.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d748b-119">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="d748b-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="d748b-120">按 CTRL+F5 以執行範例。</span><span class="sxs-lookup"><span data-stu-id="d748b-120">Press CTRL + F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d748b-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d748b-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d748b-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d748b-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d748b-123">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="d748b-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d748b-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d748b-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a><span data-ttu-id="d748b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d748b-125">See Also</span></span>  
 [<span data-ttu-id="d748b-126">內建活動程式庫</span><span class="sxs-lookup"><span data-stu-id="d748b-126">Built-In Activity Library</span></span>](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
