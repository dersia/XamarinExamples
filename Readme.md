# "Xamarin - Cross-Platform App Development" - Talk

## slides
You can find the slides, used during the Talk, inside the slides folder.
## samples
Since the sample was downloaded and not forked from the Xamarin-Samples-Repository, changes there won't refelct here. 
During the Talk we added a UWP-App to the soulution and these changes are uploaded there too.

If you want to try this out yourselves here are the steps to add the UWP-App to your Xamarin-Forms project:

  - Add a new UWP-Project to your solution using the Visual Studio-Template for Windows Universal App (Win10)
  - Add reference to the your Xamarin.Forms-PCL-Project
  - Add NuGet-Package Xamarin.Forms
  - Init Xamarin.Forms in your UWP-App App.cs
    ```CSharp
        protected override void OnLaunched(LaunchActivatedEventArgs e)
        {
            ...
            if (rootFrame == null)
            {
                // Frame erstellen, der als Navigationskontext fungiert und zum Parameter der ersten Seite navigieren
                rootFrame = new Frame();

                rootFrame.NavigationFailed += OnNavigationFailed;
                
                
                // Initilize Xamarin.Forms
                Xamarin.Forms.Forms.Init(e);
                
                
                if (e.PreviousExecutionState == ApplicationExecutionState.Terminated)
                {
                    //TODO: Zustand von zuvor angehaltener Anwendung laden
                }

                // Den Frame im aktuellen Fenster platzieren
                Window.Current.Content = rootFrame;
            }
            ...
        }
    ```
    
  - Add Xamarin.Forms xml-namespace to MainPage.xaml and change the RootElement to Xamarin.Forms.WindowsPage
    ```Xaml
        <forms:WindowsPage
            x:Class="WorkingWithPopups.UWP.MainPage"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:local="using:WorkingWithPopups.UWP"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            
            xmlns:forms="using:Xamarin.Forms.Platform.UWP"
            
            mc:Ignorable="d">

            <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        
            </Grid>
        </forms:WindowsPage>
    ```
  - Adjust the BaseClass for your MainPage to use Xamarin.Forms.WindowsPage in MainPage.xaml.cs
    ```CShar
        public sealed partial class MainPage : WindowsPage
    ```
  - Load your Xamarin.Forms-App inside your MainPage.xaml.cs
    ```CSharp
        public MainPage()
        {
            this.InitializeComponent();
            
            LoadApplication(new WorkingWithPopups.App());
            
        }
    ```
  - Build, Deploy, Debug, Have Fun!
    
If you have any questions left, don't hesitate to tweet me