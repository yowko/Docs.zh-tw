---
title: HOW TO：驗證應用程式設定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
ms.openlocfilehash: 2fef6c924498003bc9ea393ba2117a1cb5f2afab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212085"
---
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="e6487-102">HOW TO：驗證應用程式設定</span><span class="sxs-lookup"><span data-stu-id="e6487-102">How to: Validate Application Settings</span></span>
<span data-ttu-id="e6487-103">本主題示範如何在保存應用程式設定之前先行驗證。</span><span class="sxs-lookup"><span data-stu-id="e6487-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>  
  
 <span data-ttu-id="e6487-104">因為應用程式設定為強型別，對於使用者無法將型別不正確的資料指派給指定的設定這一點，您可以有些信心。</span><span class="sxs-lookup"><span data-stu-id="e6487-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="e6487-105">不過，使用者仍然可以嘗試將超出可接受界限的值指派給設定，例如，提供未來時間的出生日期。</span><span class="sxs-lookup"><span data-stu-id="e6487-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <xref:System.Configuration.ApplicationSettingsBase><span data-ttu-id="e6487-106">所有的應用程式設定類別的父類別會公開四個事件，若要啟用這類界限檢查。</span><span class="sxs-lookup"><span data-stu-id="e6487-106">, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="e6487-107">在處理這些事件時，您所有的驗證程式碼會放在單一位置，而不是零散分佈在整個專案。</span><span class="sxs-lookup"><span data-stu-id="e6487-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>  
  
 <span data-ttu-id="e6487-108">您所使用的事件取決於何時需要驗證設定，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="e6487-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>  
  
|<span data-ttu-id="e6487-109">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="e6487-109">Event</span></span>|<span data-ttu-id="e6487-110">發生時機和用途</span><span class="sxs-lookup"><span data-stu-id="e6487-110">Occurrence and use</span></span>|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="e6487-111">在初次載入設定屬性群組之後發生。</span><span class="sxs-lookup"><span data-stu-id="e6487-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="e6487-112">使用此事件可先驗證整個屬性群組的初始值，然後才將值用於應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6487-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="e6487-113">在單一設定屬性值變更之前發生。</span><span class="sxs-lookup"><span data-stu-id="e6487-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="e6487-114">使用此事件可先驗證單一屬性，然後才將它變更。</span><span class="sxs-lookup"><span data-stu-id="e6487-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="e6487-115">它可立即為使用者提供有關其動作和選擇的意見回應。</span><span class="sxs-lookup"><span data-stu-id="e6487-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="e6487-116">在單一設定屬性值變更之後發生。</span><span class="sxs-lookup"><span data-stu-id="e6487-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="e6487-117">使用此事件可在單一屬性變更後，對此屬性進行驗證。</span><span class="sxs-lookup"><span data-stu-id="e6487-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="e6487-118">除非系統需要冗長的非同步驗證程序，否則此事件很少會用於進行驗證。</span><span class="sxs-lookup"><span data-stu-id="e6487-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="e6487-119">在儲存設定屬性群組之前發生。</span><span class="sxs-lookup"><span data-stu-id="e6487-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="e6487-120">使用此事件可先驗證整個屬性群組的值，然後再儲存到磁碟中予以保存。</span><span class="sxs-lookup"><span data-stu-id="e6487-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|  
  
 <span data-ttu-id="e6487-121">一般而言，您不會在相同應用程式內將這些事件全都用於進行驗證。</span><span class="sxs-lookup"><span data-stu-id="e6487-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="e6487-122">比方說，它通常是可滿足所有驗證需求，藉由只處理<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>事件。</span><span class="sxs-lookup"><span data-stu-id="e6487-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
 <span data-ttu-id="e6487-123">當事件處理常式偵測到無效值時，它通常會執行下列其中一個動作︰</span><span class="sxs-lookup"><span data-stu-id="e6487-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>  
  
-   <span data-ttu-id="e6487-124">自動提供已知正確的值，例如預設值。</span><span class="sxs-lookup"><span data-stu-id="e6487-124">Automatically supplies a value known to be correct, such as the default value.</span></span>  
  
-   <span data-ttu-id="e6487-125">重新查詢伺服器程式碼的使用者以獲得資訊。</span><span class="sxs-lookup"><span data-stu-id="e6487-125">Re-queries the user of server code for information.</span></span>  
  
-   <span data-ttu-id="e6487-126">事件引發之前其相關聯的動作，例如<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>並<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>，會使用<xref:System.ComponentModel.CancelEventArgs>取消作業的引數。</span><span class="sxs-lookup"><span data-stu-id="e6487-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>  
  
 <span data-ttu-id="e6487-127">如需處理事件的詳細資訊，請參閱[事件處理常式概觀](../event-handlers-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="e6487-127">For more information about event handling, see [Event Handlers Overview](../event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="e6487-128">下列程序示範如何測試使用有效的出生日期<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>或<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>事件。</span><span class="sxs-lookup"><span data-stu-id="e6487-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="e6487-129">我們在撰寫這些程序時，是假設您已建立應用程式設定；在此範例中，我們會對名為 `DateOfBirth` 的設定執行界限檢查。</span><span class="sxs-lookup"><span data-stu-id="e6487-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="e6487-130">如需建立設定的詳細資訊，請參閱[How to:建立應用程式設定](how-to-create-application-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e6487-130">For more information about creating settings, see [How to: Create Application Settings](how-to-create-application-settings.md).</span></span>  
  
### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="e6487-131">取得應用程式設定物件</span><span class="sxs-lookup"><span data-stu-id="e6487-131">To obtain the application settings object</span></span>  
  
-   <span data-ttu-id="e6487-132">請完成下列其中一項來取得應用程式設定物件 (包裝函式執行個體) 的參考︰</span><span class="sxs-lookup"><span data-stu-id="e6487-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>  
  
    -   <span data-ttu-id="e6487-133">如果您是使用**屬性編輯器**中的 [Visual Studio 應用程式設定] 對話方塊來建立您的設定，您可以透過下列運算式擷取針對您的語言所產生的預設設定物件。</span><span class="sxs-lookup"><span data-stu-id="e6487-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         <span data-ttu-id="e6487-134">-或-</span><span class="sxs-lookup"><span data-stu-id="e6487-134">-or-</span></span>  
  
    -   <span data-ttu-id="e6487-135">如果您是 Visual Basic 開發人員，並且使用專案設計工具來建立應用程式設定，您可以使用 [My.Settings 物件](~/docs/visual-basic/language-reference/objects/my-settings-object.md)來擷取您的設定。</span><span class="sxs-lookup"><span data-stu-id="e6487-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
         <span data-ttu-id="e6487-136">-或-</span><span class="sxs-lookup"><span data-stu-id="e6487-136">-or-</span></span>  
  
    -   <span data-ttu-id="e6487-137">如果您建立您的設定，藉由衍生自<xref:System.Configuration.ApplicationSettingsBase>直接，您需要以手動方式將您的類別具現化。</span><span class="sxs-lookup"><span data-stu-id="e6487-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 <span data-ttu-id="e6487-138">我們在撰寫下列程序時，是假設您已透過完成此程序中的最後一項來取得應用程式設定物件。</span><span class="sxs-lookup"><span data-stu-id="e6487-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="e6487-139">在有設定變更時驗證應用程式設定</span><span class="sxs-lookup"><span data-stu-id="e6487-139">To validate Application Settings when a setting is changing</span></span>  
  
1.  <span data-ttu-id="e6487-140">如果您是C#開發人員，在表單或控制項的`Load`事件，加入事件處理常式<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>事件。</span><span class="sxs-lookup"><span data-stu-id="e6487-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
     <span data-ttu-id="e6487-141">-或-</span><span class="sxs-lookup"><span data-stu-id="e6487-141">-or-</span></span>  
  
     <span data-ttu-id="e6487-142">如果您是 Visual Basic 開發人員，您應該使用 `WithEvents` 關鍵字來宣告 `Settings` 變數。</span><span class="sxs-lookup"><span data-stu-id="e6487-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingChanging += new SettingChangingEventHandler(MyCustomSettings_SettingChanging);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(sender as Object, e as EventArgs)  
        AddHandler settings.SettingChanging, AddressOf MyCustomSettings_SettingChanging  
    End Sub   
    ```  
  
2.  <span data-ttu-id="e6487-143">定義事件處理常式，並在其內部撰寫程式碼以執行出生日期界限檢查。</span><span class="sxs-lookup"><span data-stu-id="e6487-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
    ```csharp  
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)  
    {  
        if (e.SettingName.Equals("DateOfBirth")) {  
            Date newDate = (Date)e.NewValue;  
            If (newDate > Date.Now) {  
                e.Cancel = true;  
                // Inform the user.  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingChanging(sender as Object, e as SettingChangingEventArgs) Handles Settings.SettingChanging  
        If (e.SettingName.Equals("DateOfBirth")) Then  
            Dim NewDate as Date = CType(e.NewValue, Date)  
            If (NewDate > Date.Now) Then  
                e.Cancel = True  
                ' Inform the user.  
            End If  
        End If  
    End Sub  
    ```  
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="e6487-144">在發生儲存時驗證應用程式設定</span><span class="sxs-lookup"><span data-stu-id="e6487-144">To validate Application Settings when a Save occurs</span></span>  
  
1.  <span data-ttu-id="e6487-145">在您的表單或控制項的`Load`事件，加入事件處理常式<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>事件。</span><span class="sxs-lookup"><span data-stu-id="e6487-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingsSaving += new SettingsSavingEventHandler(MyCustomSettings_SettingsSaving);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(Sender as Object, e as EventArgs)  
        AddHandler settings.SettingsSaving, AddressOf MyCustomSettings_SettingsSaving  
    End Sub  
    ```  
  
2.  <span data-ttu-id="e6487-146">定義事件處理常式，並在其內部撰寫程式碼以執行出生日期界限檢查。</span><span class="sxs-lookup"><span data-stu-id="e6487-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
    ```csharp  
    private void MyCustomSettings_SettingsSaving(Object sender, SettingsSavingEventArgs e)  
    {  
        if (this["DateOfBirth"] > Date.Now) {  
            e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingsSaving(Sender as Object, e as SettingsSavingEventArgs)  
        If (Me["DateOfBirth"] > Date.Now) Then  
            e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e6487-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6487-147">See also</span></span>

- [<span data-ttu-id="e6487-148">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="e6487-148">Creating Event Handlers in Windows Forms</span></span>](../creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="e6487-149">HOW TO：建立應用程式設定</span><span class="sxs-lookup"><span data-stu-id="e6487-149">How to: Create Application Settings</span></span>](how-to-create-application-settings.md)
