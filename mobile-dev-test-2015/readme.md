# Mobile Dev + Test 2015
Scripting with Xamarin.UITest
===================================

This quickstart shows you the easiest way to create a basic test in C# for your Android application with Xamarin.UITest.

The project relies on two NuGet packages: 
* [NUnit](https://www.nuget.org/packages/NUnit/): a unit test runner and framework for .NET
* [Xamarin.UITest](https://www.nuget.org/packages/Xamarin.UITest/): our C#-based UI testing framework for testing locally and in Xamarin Test Cloud

## Setting your API Key
Your API key for Xamarin Test Cloud is required if you wish to run on physical devices, or for test sessions longer than 15 minutes. You can find your API Key using the following instructions:

1. Log in to the [Xamarin Test Cloud portal](http://testcloud.xamarin.com).
2. Find your name in the upper right. Click it, and go to **Account Settings**.
3. On the lower left, find the organization you want to upload tests for, and click **Teams and Apps**. 
4. Click **Show API Key** for the team you want to upload tests to. API keys in Xamarin Test Cloud are shared per team.
5. Replace the empty string in `Constants.cs` with your API key. There are also [other options for setting your API key](http://developer.xamarin.com/guides/testcloud/uitest/setting-the-api-key/), which we encourage you to check out. 

## Modifying this sample
1. Clone the repo or download the archive.
2. In `Constants.cs`, change your API Key (see Finding Your API Key section above)
3. In `Constants.cs`, change the path to point to the location of your desired Android `.apk` bundle on disk.

## Running the test locally
1. Start an Android emulator or plug in a physical device. The device should be in the list when you type `adb devices` at a terminal.
2. Open the solution in Xamarin Studio or Visual Studio.
3. Run unit tests from the IDE. You can also do this from a console window after building the solution by typing `nunit-console.exe pathToTestDllFolder` at a command prompt.

Scripting with Calabash-Cucumber
===================================
##Purpose of a GemFile
Gemfiles are used to define which gem version the tests will run. They are helpful in standardizing test runs across multiple users and on Xamarin Test Cloud. A `bundle init` will create the initial Gemfile, once created open the Gemfile with a text editor and input the desired version. `bundle update` will create a Gemfile.lock and using `bundle exec` in front of the next command will set the command to run with the Gemfile.lock.

##Using a Cucumber.yml
Cucumber.yml files let you configure your tests. [Check here for more detailed info](https://github.com/cucumber/cucumber/wiki/cucumber.yml).

##Running the test locally
Open the terminal and navigate to the directory containing the features file.
Use `bundle exec calabash-android run <path-to-apk>` optionally add `-p <profile>` if you have a profile in your cucumber.yml file.

Uploading this test to Xamarin Test Cloud
===================================
Detailed instructions are available in the [Submitting Tests documentation](http://developer.xamarin.com/guides/testcloud/submitting/).

1. Log in to [Xamarin Test Cloud](http://testcloud.xamarin.com) and click **New Test Run** in the upper right.
2. Select **New Android app** and choose your team.
3. Follow the instructions until you have a command line to execute.
4. Modify the paths and execute the command line. 

## What's next?
Now that you have a functioning environment set up for Xamarin.UITest, and have successfully uploaded a test, you can now start inspecting more about your app. A suggested next step is to add `app.Repl()` to the first line of the `BasicTest`, which will pop up a REPL window and allow you to interact with the app using various commands such as `tree`.

## Troubleshooting
Most issues with Xamarin.UITest and Android are related to your Android SDK installation. You need to have the [Android SDK platform-tools](http://developer.android.com/tools/sdk/tools-notes.html) installed (which includes adb) as well as an emulator of your choice (try out the [Xamarin Android Player preview](http://www.xamarin.com/android-player))!

|**Issue**|**What to Do**|
|-----|----------|
|I don't have an Android player installed|Install the Android SDK, or install the Xamarin Android Player|
|I receive errors related to resigning the app or a keystore issue|[Ensure your keystore is properly configured](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/publishing_an_application/part_1_-_preparing_an_application_for_release/#Create_a_New_Keystore)|
|I receive a message about my subscription when trying to upload a new test|Contact your Xamarin account manager|
