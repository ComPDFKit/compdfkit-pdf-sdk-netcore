# Introduction

[ComPDFKit PDF SDK](https://www.compdf.com) is a robust PDF library, which offers comprehensive functions for quickly viewing, annotating, editing, and signing PDFs. It is feature-rich and battle-tested, making PDF files process and manipulation easier and faster.

# Related

- [ComPDFKit API Library for .Net](https://github.com/ComPDFKit/compdfkit-api-.net)
- Download [ComPDFKit PDF SDK for .NET Core](https://www.nuget.org/packages/ComPDFKit.NetCore) in Nuget
- Download [ComPDFKit PDF SDK for .NETFramework](https://www.nuget.org/packages/ComPDFKit.NetFramework) in Nuget
- [How to Build a Windows PDF Viewer or Editor](https://www.compdf.com/blog/build-a-windows-pdf-viewer-or-editor)
- [Brief Introduction to ComPDFKit for Windows](https://www.compdf.com/blog/compdfkit-for-windows)

# Get Started for Windows


## Requirements

- Visual Studio

  Make sure that the `.NET Core cross-platform development` workload and `MSBUILD` are part of your installation.

  This guide will use Visual Studio 2022. If you would like to use the NuGet integration for Windows x64 please make sure you have Visual Studio 2017 or later.

  **Note:** ComPDFKit PDF SDK is multi-targeting. Target Frameworks: .NET Core 2.1+, .NET Standard 2.0, .NET 5, .NET 6, .NET 7, .NET 8.

- ComPDFKit 's .NET Core PDF Library for Windows:

  Please [contact us]( https://www.compdf.com/contact-sales ) to get the ComPDFKit PDF SDK for .NET Core.

- ComPDFKit PDF SDK license

  Commercial license keys are required for use in production environments. If you do not have a valid license key, please [contact us]( https://www.compdf.com/contact-sales) to obtain the license key.

  License keys are uniquely generated. Please make sure that it is not publicly available (e.g. in your public GitHub).

## Run the Samples

1. Open the solution file 'Example. sln' in Visual Studio.
2. Select a sample project in Solution Explorer and set it as the startup project. CS and VB examples are currently available.
3. Build and run the example.

Or you can open the command line tool in the project folder and run the example through the command:

```bash
dotnet run
```

## Integrate into Your Application

#### Integrate Manually

1. Open a new instance of Visual Studio 2022and create a new .NET Core console application project (`File > New > Project...` ). You can find this under the Visual C# menu.

   Click on OK and allow the IDE to create the project.

   

2. Find the Solution Explorer on the right side of the screen. Select the project and press `Alt + Enter`. This will open the properties tab.

   Alternatively, you can right click on the project and find the properties option.

   Select **.NET Core 2.1 (or above)** as the target framework for your application.

   If you are using a Windows x64 machine for your .NET Core development, you can use NuGet package manager to get the ComPDFKit PDF SDK. Otherwise, please integrate the SDK manually.

3. Right-click "Dependencies" and click "Add Project Reference", which will open the "Reference Manager" dialog box. Click the option at the bottom of the dialog box, find the corresponding "ComPDFKit.NET.dll", select it and click Add.

4. In the Solution Explorer, select the project and press `Shift + Alt + A`. With this you can Add an Existing Item.

   Alternatively, you can right click on the project and find the `Add an existing item...` option under the `Add` submenu.

   Navigate to the library location again, select the file type as `All Files (*.*)` and select `ComPDFKitNative.dll`. Click Add.

5. Select  ComPDFKit.NET.dll  in the solution explorer. A properties window should appear below. In it, change the Build Action setting to `Content` and the Copy to Output Directory setting to `Copy always`. To avoid errors, use the drop-down menus available for those fields.

#### Integrate with NuGet

1. Perform the first 2 steps of integrating manually.

2. Right click on project Dependencies and click on `Manage NuGet Packages...`. This will open the NuGet Package Manager

3. Click on the `Browse` tab near the top of the package manager. In the search bar enter:

   ```
   ComPDFKit.NetCore
   ```

4. Select the `ComPDFKit.NetCore` package by PDF Tecnologies Inc. and click on the `Install` button in the panel with the package information. If you're prompted or an external dialog is opened for confirmation, click on `Ok`.

   After installation, you will see the reference to the package under Dependencies in Solution Explorer.

#### Create PDF Document

We have completed all the preparation steps. Now let's use the ComPDFKit PDF SDK to create a PDF file with a blank page, and replace your Program. cs file with the following code. Note that you need to replace your license in the 'LicenseVerify()' method.

```csharp
using ComPDFKit.NativeMethod;
using ComPDFKit.PDFDocument;
using Microsoft.Win32;
using System.Reflection.Metadata;
using System.Windows;

namespace ComPDFKit_Demo
{
    public class Program
    {
        private static bool LicenseVerify()
        {
            if (!CPDFSDKVerifier.LoadNativeLibrary())
                return false;
            LicenseErrorCode verifyResult = CPDFSDKVerifier.LicenseVerify("Input your license here");
            return (verifyResult == LicenseErrorCode.E_LICENSE_SUCCESS);
        }
        
        public static void Main()
        { 
            LicenseVerify();
            CPDFDocument document = CPDFDocument.CreateDocument();
             // Insert to the first page
			int pageIndex = 0;
			int pageWidth = 595;
			int pageHeight = 842;
			//The InsertPage method can specify an image path. When the image path is empty, a blank page will be inserted.
			document.InsertPage(pageIndex, pageWidth, pageHeight, "");
			document.WriteToFilePath("new_file.pdf");// Save the entire document object to the current path.
            Console.WriteLine("Done. Results saved in new_file.pdf");
        }
    }
}
```

After running the program, please check the output file generated by the program. You will find that a PDF file with blank pages has been generated, and by default, it should be in the bin/Debug directory where your project files are located.

# Get Started for Linux

## Requirements

- NET Core SDK
  **Note:** ComPDFKit PDF SDK is multi-targeting. Target Frameworks : .NET Core 2.1+, .NET Standard 2.0, .NET 5, .NET 6, .NET 7, .NET 8。

- ComPDFKit 's .NET Core PDF Library for Linux:
  Please [contact us ](https://www.compdf.com/contact-sales )to obtain the ComPDFKit PDF SDK for NET Core.

- ComPDFKit PDF SDK license

  Commercial license keys are required for use in production environments. If you do not have a valid license key, please [contact us]( https://www.compdf.com/contact-sales) to obtain the license key.

  License keys are uniquely generated. Please make sure that it is not publicly available (e.g. in your public GitHub).

## Run the Samples

Enter the sample folder and run the example from the command line:

- Input/ Run. sh all to run all examples.
- Input/ Run. sh<samplename>Run a specific example. For example/ Run. sh BatesTest.

If you receive an error message bash:/ Test. sh: Permission denied, you need to enter the following command:

```shell
chmod+x run .sh
```

## Integrate into Your Application

You can follow the manual or nuget integration described below for operation. This section will help you build your first ComPDFKit application. If you can open, save, and close PDFDoc, you can easily integrate the rest of the ComPDFKit PDF SDK.

### Integrate Manually

1. Create a new project named ComPDFKit Demo_ through the console:

   ```shell
   mkdir ComPDFKitDemo
   cd ComPDFKitDemo
   dotnet new console -o "ComPDFKit Demo"
   ```

2. Copy the ComPDFKitNative.so file and ComPDFKit Copy the NET.dll file to the project folder.

3. Add the following code to the. csproj file:

   ```xml
   <ItemGroup>
    <Reference Include="ComPDFKit.NET.dll">
      <HintPath>ComPDFKit.NET.dll</HintPath>
    </Reference>
   </ItemGroup>
   
   <ItemGroup>
       <Content Include="ComPDFKitNative.so">
           <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
       </Content>
   </ItemGroup>
   ```

   Your final ComPDFKit Demo.csproj file should look like this:

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
   
       <PropertyGroup>
           <OutputType>Exe</OutputType>
           <TargetFramework>net6.0</TargetFramework>
       </PropertyGroup>
   
       <ItemGroup>
           <Reference Include="ComPDFKit.NET.dll">
               <HintPath>ComPDFKit.NET.dll</HintPath>
           </Reference>
       </ItemGroup>
   
       <ItemGroup>
           <Content Include="ComPDFKitNative.so">
               <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
           </Content>
       </ItemGroup>
   
   </Project>
   ```

### Integrate with NuGet

1. Create a new project named ComPDFKit Demo_ through the console:

   ```shell
   mkdir ComPDFKitDemo
   cd ComPDFKitDemo
   dotnet new console -o "ComPDFKit Demo"
   ```

2. Enter the project folder and install ComPDFKit Core NuGet package:

   ```bash
   dotnet add package ComPDFKit.NetCore
   ```

### Create PDF Document

We have completed all the preparation steps. Now let's use the ComPDFKit PDF SDK to create a PDF file with a blank page, and replace your Program. cs file with the following code. Note that you need to replace your license in the 'LicenseVerify()' method.

```csharp
using ComPDFKit.NativeMethod;
using ComPDFKit.PDFDocument;
using System.Reflection.Metadata;

namespace ComPDFKit_Demo
{
    public class Program
    {
        private static bool LicenseVerify()
        {
            if (!CPDFSDKVerifier.LoadNativeLibrary())
                return false;
            LicenseErrorCode verifyResult = CPDFSDKVerifier.LicenseVerify("Input your license here");
            return (verifyResult == LicenseErrorCode.E_LICENSE_SUCCESS);
        }
        
        public static void Main()
        { 
            LicenseVerify();
            CPDFDocument document = CPDFDocument.CreateDocument();
			int pageIndex = 0;
			int pageWidth = 595;
			int pageHeight = 842;
			document.InsertPage(pageIndex, pageWidth, pageHeight, "");
			document.WriteToFilePath("new_file.pdf");
            Console.WriteLine("Done. Results saved in new_file.pdf");
        }
    }
}
```

Now you can run the program from the command line:

```bash
dotnet run
```

Now you will find the 'new_file. pdf' file in the program output directory, which is a PDF file with a blank page.

# Get Started for macOS

## Requirements

- .NET Core SDK

  **Note:** ComPDFKit PDF SDK is multi-targeting. Target Frameworks : .NET Core 2.1+, .NET Standard 2.0, .NET 5, .NET 6, .NET 7, .NET 8。

- ComPDFKit 's .NET Core PDF Library for macOS:
  Please [contact us ](https://www.compdf.com/contact-sales )to obtain the ComPDFKit PDF SDK for NET Core.

- ComPDFKit PDF SDK license

  Commercial license keys are required for use in production environments. If you do not have a valid license key, please [contact us]( https://www.compdf.com/contact-sales) to obtain the license key.

  License keys are uniquely generated. Please make sure that it is not publicly available (e.g. in your public GitHub).

## Run the Samples

Enter the sample folder and run the example from the command line:

- Input/ Run. sh all to run all examples.
- Input/ Run. sh<samplename>Run a specific example. For example/ Run. sh BatesTest.

If you receive an error message bash:/ Test. sh: Permission denied, you need to enter the following command:

```
chmod +x run.sh
```

## Integrate into your Application

You can follow the manual or nuget integration described below for operation. This section will help you build your first ComPDFKit application. If you can open, save, and close PDFDoc, you can easily integrate the rest of the ComPDFKit PDF SDK.

### Integrate Manually

1. Create a new project named ComPDFKit Demo_ through the console

   ```
   mkdir ComPDFKitDemo
   cd ComPDFKitDemo
   dotnet new console -o "ComPDFKit Demo"
   ```

2. Copy the libComPDFKit.dylib file and the ComPDFKit.Desk.Core.dll file to the project folder.

3. Add the following code to the .csproj file:

   ```xml
   <ItemGroup>
       <Reference Include="ComPDFKit.NET.dll">
           <HintPath>ComPDFKit.Desk.Core.dll</HintPath>
       </Reference>
   </ItemGroup>
   
   <ItemGroup>
       <Content Include="libComPDFKit.dylib">
           <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
       </Content>
   </ItemGroup>
   ```

   Your final ComPDFKit Demo.csproj file should look like this:

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
   
       <PropertyGroup>
           <OutputType>Exe</OutputType>
           <TargetFramework>net6.0</TargetFramework>
       </PropertyGroup>
   
       <ItemGroup>
           <Reference Include="ComPDFKit.Desk.Core.dll">
               <HintPath>ComPDFKit.Desk.Core.dll</HintPath>
           </Reference>
       </ItemGroup>
   
       <ItemGroup>
           <Content Include="libComPDFKit.dylib">
               <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
           </Content>
       </ItemGroup>
   
   </Project>
   ```

### Integrate with NuGet

1. Create a new project named ComPDFKit Demo in the console:

   ```shell
   mkdir ComPDFKitDemo
   cd ComPDFKitDemo
   dotnet new console -o "ComPDFKit Demo"
   ```

2. Go to the project folder and install the ComPDFKit.Core NuGet package:

   ```bash
   dotnet add package ComPDFKit.NetCore
   ```

### Create PDF Document

We have completed all the preparation steps. Now let us use ComPDFKit PDF SDK to create a PDF file with a blank page. Replace your Program.cs file with the following code. Note: You need to replace your license into the `LicenseVerify()` method.

```csharp
using ComPDFKit.NativeMethod;
using ComPDFKit.PDFDocument;
using System.Reflection.Metadata;

namespace ComPDFKit_Demo
{
    public class Program
    {
        private static bool LicenseVerify()
        {
            if (!CPDFSDKVerifier.LoadNativeLibrary())
                return false;
            LicenseErrorCode verifyResult = CPDFSDKVerifier.LicenseVerify("Input your license here");
            return (verifyResult == LicenseErrorCode.E_LICENSE_SUCCESS);
        }
        
        public static void Main()
        { 
            LicenseVerify();
            CPDFDocument document = CPDFDocument.CreateDocument(); 
			int pageIndex = 0;
			int pageWidth = 595;
			int pageHeight = 842; 
			document.InsertPage(pageIndex, pageWidth, pageHeight, "");
			document.WriteToFilePath("new_file.pdf");
            Console.WriteLine("Done. Results saved in new_file.pdf");
        }
    }
}
```

Now you can run the program from the command line:

```shell
dotnet run
```

You will now find the `new_file.pdf` file in the program output directory, which is a PDF file with a blank page.

# Support

[ComPDFKit]((https://www.compdf.com)) has a professional R&D team that produces comprehensive technical documentation and guides to help developers. Also, you can get an immediate response when reporting your problems to our support team.

- For detailed information, please visit our [Guides](https://www.compdf.com/guides/pdf-sdk/windows/overview) page.

- Stay updated with the latest improvements through our [Changelog](https://www.compdf.com/pdf-sdk/changelog-windows).

- For technical assistance, please reach out to our [Technical Support](https://www.compdf.com/support).

- To get more details and an accurate quote, please contact our [Sales Team](https://compdf.com/contact-us).




# License

ComPDFKit PDF SDK supports flexible licensing options, please contact [our sales team](mailto:support@compdf.com) to know more. Each license is only valid for one application ID in development mode.  However, any documents, sample code, or source code distribution from the released package of ComPDFKit PDF SDK to any third party is prohibited.



# Note

We are glad to announce that you can register a ComPDFKit API account for a [free trial](https://api.compdf.com/api/pricing) to process 1000 documents per month for free.
