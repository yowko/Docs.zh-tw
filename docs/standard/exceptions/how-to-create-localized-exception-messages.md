---
title: 如何通過當地語系化的異常消息創建使用者定義的異常
description: 瞭解如何使用當地語系化的異常消息創建使用者定義的異常
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 5a02c71b16e2c8e5ade5128866af7dc46a03ba4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160179"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="bd1f3-103">如何通過當地語系化的異常消息創建使用者定義的異常</span><span class="sxs-lookup"><span data-stu-id="bd1f3-103">How to create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="bd1f3-104">在本文中，您將學習如何使用附屬程式集創建從基<xref:System.Exception>類繼承的使用者定義的異常，並帶有當地語系化的異常消息。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="bd1f3-105">創建自訂異常</span><span class="sxs-lookup"><span data-stu-id="bd1f3-105">Create custom exceptions</span></span>

<span data-ttu-id="bd1f3-106">.NET 包含許多可以使用的不同異常。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="bd1f3-107">但是，在某些情況下，當它們都無法滿足您的需求時，您可以創建自己的自訂異常。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="bd1f3-108">假設您要創建`StudentNotFoundException`一個`StudentName`包含屬性。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="bd1f3-109">要創建自訂異常，請按照以下步驟操作：</span><span class="sxs-lookup"><span data-stu-id="bd1f3-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="bd1f3-110">創建從 繼承的<xref:System.Exception>可序列化類。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="bd1f3-111">類名稱應以"異常"結尾：</span><span class="sxs-lookup"><span data-stu-id="bd1f3-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. <span data-ttu-id="bd1f3-112">添加預設建構函式：</span><span class="sxs-lookup"><span data-stu-id="bd1f3-112">Add the default constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. <span data-ttu-id="bd1f3-113">定義任何其他屬性和建構函式：</span><span class="sxs-lookup"><span data-stu-id="bd1f3-113">Define any additional properties and constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a><span data-ttu-id="bd1f3-114">創建當地語系化的異常消息</span><span class="sxs-lookup"><span data-stu-id="bd1f3-114">Create localized exception messages</span></span>

<span data-ttu-id="bd1f3-115">您已經創建了自訂異常，並且可以使用如下代碼將其扔到任何位置：</span><span class="sxs-lookup"><span data-stu-id="bd1f3-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

<span data-ttu-id="bd1f3-116">上一行的問題是，`"The student cannot be found."`這只是一個常量字串。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="bd1f3-117">在當地語系化應用程式中，您希望根據使用者區域性使用不同的消息。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="bd1f3-118">[衛星元件](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)是做到這一點的好方法。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="bd1f3-119">附屬程式集是包含特定語言資源的 .dll。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="bd1f3-120">當您在運行時請求特定資源時，CLR 會根據使用者區域性找到該資源。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="bd1f3-121">如果未找到該區域性的附屬程式集，則使用預設區域性的資源。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="bd1f3-122">要創建當地語系化的異常消息，</span><span class="sxs-lookup"><span data-stu-id="bd1f3-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="bd1f3-123">創建名為 *"資源"* 的新資料夾以保存資源檔。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="bd1f3-124">向其添加新資源檔。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-124">Add a new resource file to it.</span></span> <span data-ttu-id="bd1f3-125">要在 Visual Studio 中執行此操作，請按右鍵**解決方案資源管理器**中的資料夾**Add** > ，然後選擇"**添加新專案** > **資源檔**"。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="bd1f3-126">命名檔*例外消息.resx*. 。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="bd1f3-127">這是預設資源檔。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-127">This is the default resources file.</span></span>
1. <span data-ttu-id="bd1f3-128">為異常消息添加名稱/值對，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="bd1f3-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![將資源添加到預設區域性](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="bd1f3-130">為法語添加新的資源檔。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-130">Add a new resource file for French.</span></span> <span data-ttu-id="bd1f3-131">將其命名為*ExceptionMessages.fr-FR.resx*。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="bd1f3-132">再次為異常消息添加名稱/值對，但使用法語值：</span><span class="sxs-lookup"><span data-stu-id="bd1f3-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![將資源添加到 fr-FR 區域性](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="bd1f3-134">生成專案後，生成輸出檔案夾應包含帶 *.dll*檔的*fr-FR*資料夾，該檔是附屬程式集。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="bd1f3-135">使用如下代碼引發異常：</span><span class="sxs-lookup"><span data-stu-id="bd1f3-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > <span data-ttu-id="bd1f3-136">`TestProject`如果專案名稱為，並且資源檔*ExceptionMessages.resx*駐留在專案的 *"資源"* 資料夾中，則資源檔的完全限定名稱為`TestProject.Resources.ExceptionMessages`。</span><span class="sxs-lookup"><span data-stu-id="bd1f3-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd1f3-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd1f3-137">See also</span></span>

- [<span data-ttu-id="bd1f3-138">如何創建使用者定義的異常</span><span class="sxs-lookup"><span data-stu-id="bd1f3-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="bd1f3-139">建立桌面應用程式的附屬組件</span><span class="sxs-lookup"><span data-stu-id="bd1f3-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="bd1f3-140">base (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bd1f3-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="bd1f3-141">this (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bd1f3-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
