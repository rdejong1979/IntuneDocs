---
# required metadata

title: Prerequisites for mobile device enrollment | Microsoft Intune
description: Set up mobile device management (MDM) prerequisites and get ready to enroll different operating systems.
keywords:
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: damionw
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Prerequisites for mobile device management in Intune
You can enable employees to enroll their mobile devices with Intune requires the following steps. These same steps are required to manage company-owned devices.

|Steps|Details|  
|-----------|-------------|  
|**Step 1:** [Enable connections](#step-1-enable-connections)|Ensure your custom domain name is configured and network communication is ready|  
|**Step 2:** [Set MDM authority](#step-2-set-mdm-authority)|The mobile device management authority defines the service assigned to your devices|
|**Step 3:** [Create groups](#step-3-create-groups)|Configure user-facing settings for the Company Portal app|  
|**Step 4:** [Configure Company Portal](#step-4-configure-company-portal)|Configure user-facing settings for the Company Portal app|  
|**Step 5:** [Assign user licenses](#step-5-assign-user-licenses)|Assign Intune licenses to users so they can enroll devices|
|**Step 6:** [Enable enrollment](#step-6-enable-enrollment)|Enable platform-specific settings for iOS and Windows management. Android devices need no additional configuration.|
|**Step 7:** [Next steps](#step-7-next-steps)|Enable platform-specific settings for iOS and Windows management. Android devices need no additional configuration.|

Looking for Intune with Configuration Manager?
> [!div class="button"]
[View SCCM docs >](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm)

## Step 1: Enable connections

Before you enable mobile device enrollment, be sure you've done the following:
- [Review required network URLs and ports](../get-started/network-infrastructure-requirements-for-microsoft-intune)
- [Add and verify your domain name](../get-started/domain-names-for-microsoft-intune)

## Step 2: Set MDM authority
The MDM authority defines the management service that has permission to manage a set of devices. The options for the MDM authority include Intune by itself and Configuration Manager with Intune. If you set Configuration Manager as the management authority, no other service can be used for mobile device management.

>[!IMPORTANT]
> Consider carefully whether you want to manage mobile devices by using Intune only (online service) or System Center Configuration Manager with Intune (on-premises software solution in conjunction with the online service). After you set the mobile device management authority, this cannot be changed.



1.  In the [Microsoft Intune administration console](http://manage.microsoft.com), choose **Admin** &gt; **Mobile Device Management**.

2.  In the **Tasks** list, click **Set Mobile Device Management Authority**. The **Set MDM Authority** dialog box opens.

    ![Set MDM authority dialog box](../media/intune-mdm-authority.png)

3.  Intune requests confirmation that you want Intune as your MDM authority. Select the check box, and then choose **Yes** to use Microsoft Intune to manage mobile devices.

## Step 3: Create groups

You can create user and device groups to simplify management and improve targeting of deployed apps, policies, and company resources. [Learn how to create groups](use-groups-to-manage-users-and-devices-with-microsoft-intune.md#create-groups).

## Step 4: Configure Company Portal

The Intune Company Portal is where users access company data and can do common tasks like enrolling devices, installing apps, and locating information for assistance from your IT department.

> [!TIP]
> When you customize the Company Portal, the configurations apply to both the Company Portal website and Company Portal apps.

Customizing the Company Portal helps to provide a familiar and helpful experience for your end users. To do this, just sign in to the [Microsoft Intune administration console](https://manage.microsoft.com) as a tenant or service administrator, choose **Admin** &gt; **Company Portal**, and configure the Company Portal settings.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### Company contact information and privacy statement

The company name is displayed as the Company Portal title. The contact information and details are displayed to users in the Contact IT screen of the Company Portal. The privacy statement is displayed when a user clicks the privacy link.

|Field name|Max length|More information|
    |----------|------------------------|----------------|
    |Company name|40|This name is displayed as the title of the Company Portal. **Note**: Alpha-numeric characters only. This field doesn't support special characters.|
    |IT department contact name|40|This name is displayed on the **Contact IT** page.|
    |IT department phone number|20|This contact number is displayed on the **Contact IT** page.|
    |IT department email address|40|This contact address is displayed on the **Contact IT** page. You must enter a valid email address in the format **alias@domainname.com**.|
    |Additional information|120|This information is displayed on the **Contact IT** page.|
    |Company privacy statement URL|79|You can specify your own company privacy statement that appears when users click the privacy links from the Company Portal. You must enter a valid URL in the format https://www.contoso.com.|

### Support contacts
The support website is displayed to users in the Company Portal to enable them to access online support.

|Field name|Max length|More information|
    |----------|------------------------|----------------|
    |Support website URL|150|If you have a support website that you want your users to use, specify the URL here. The URL must be in the format https://www.contoso.com. If you don't specify a URL, nothing is displayed for the support website on the **Contact IT** page in the Company Portal.|
    |Website name|40|This name is the friendly name that is displayed for the URL to the support website. If you specify a support website URL and no friendly name, then **Go to IT website** is displayed on the **Contact IT** page in the Company Portal.|


### Company branding customization

You can customize your Company Portal with your company logo, company name, theme color, and background.

|Field name|More information|
    |----------|----------------|
    |Theme color|Select a theme color to apply to the Company Portal.|
    |Include company logo|When you enable this option, you can upload your company logo to show in your Company Portal. You can upload two logos: one logo that is displayed when the Company Portal background is white, and one logo that is displayed when the Company Portal background uses your selected theme color. Each logo must be a .png or .jpg file, have a maximum resolution of 400 x 100 pixels, and be 750 KB or less in size.|
    |Choose a background for the Company Portal app|This setting affects the background for the Company Portal app only.|


After you save your changes, you can use the links that are provided at the bottom of the **Company Portal** page of the administration console to view the Company Portal website. These links cannot be changed. When a user signs in, these links display your subscriptions in the Company Portal.

## Step 5: Assign user licenses

You use the **Office 365 management portal** to manually add cloud-based users and assign licenses to both cloud-based user accounts and accounts that are synchronized from your on-premises Active Directory to Azure Active Directory (Azure AD). You can [synchronize on-premises users to Azure AD](../get-started/domain-names-for-microsoft-intune#to-synchronize-on-premises-users-with-azure-ad.md).

1.  Sign in to the [Office 365 management portal](https://portal.office.com/Admin/Default.aspx) by using your tenant administrator credentials.

2.  Select the user account that you want to assign an Intune user license to, and then select the **Microsoft Intune** check box on the user account properties.

3.  The user account will now be added to the Microsoft Intune user group, which grants the user permissions to use the service and enroll their devices into management.

### To synchronize on-premises users with Azure AD

1. [Add the UPN suffix](https://technet.microsoft.com/en-us/library/cc772007.aspx) for your custom domain in your on-premises Active Directory.
2. Set the new UPN suffix for the on-premises users that you plan to import.
3. Run [Azure AD Connect sync](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) to integrate your on-premises users with Azure AD.
4. Once the user account information has successfully synchronized, you can then assign Microsoft Intune licenses using the [Office 365 Management Portal](https://portal.office.com/Admin/Default.aspx).

## Step 6: Enable enrollment
After setting up the MDM authority, you need to set up device management for the operating systems that your organization wants to support. The steps that are required to set up device management vary by operating system. For example, the Android OS does not require you to do anything in the Intune administration console. On the other hand, Windows and iOS require a trust relationship between devices and Intune to allow management.

Set up management for the following platforms:
- [iOS and Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Android](set-up-android-management-with-microsoft-intune.md)
- [Android for Work](set-up-android-for-work.md)
- [Windows PCs and laptops](set-up-windows-device-management-with-microsoft-intune.md)
- [Windows 10 Mobile and Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)

You can also enable [enrollment of corporate-owned devices](manage-corporate-owned-devices).

## Step 7: Next steps

Now that enrollment is enabled, you should set up management to meet your business's needs. The following are some  management options:

- [Deploy policies that manage settings and features on devices](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
- [Enable access to company resources like email, Wi-Fi, and VPN](enable-access-to-company-resources-with-microsoft-intune.md)
- [Add apps](add-apps.md) and [deploy app](deploy-apps.md) to managed devices
- [Create device compliance policies](introduction-to-device-compliance-policies-in-microsoft-intune.md) and [restrict access based on compliance](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
