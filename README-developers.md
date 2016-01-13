NuGet package management
===

## Create NuGet packages

### Example 4.1.2 RC

```
cd nlog/src
msbuild NLog.proj /t:rebuild /t:NuGetPackage  /p:BuildLastMajorVersion=4.0.0 /p:AssemblyFileVersion=4.1.2.443 /p:BuildVersion=4.1.2-rc /p:configuration=release /p:BuildLabelOverride=NONE
```

### Example 4.1.2 (RTM)

```
cd nlog/src
msbuild NLog.proj /t:rebuild /t:NuGetPackage  /p:BuildLastMajorVersion=4.0.0 /p:AssemblyFileVersion=4.1.2.444 /p:BuildVersion=4.1.2 /p:configuration=release /p:BuildLabelOverride=NONE
```

## Publish symbols packages

To www.symbolsource.org

```
nuget push NLog\build\bin\release\NuGetPackages\NLog.4.2.0.symbols.nupkg
nuget push NLog\build\bin\release\NuGetPackages\NLog.Extended.4.2.0.symbols.nupkg
```

## Versions

- "BuildLastMajorVersion" should be `major.0.0`. In NLog 4.x - 4.y: 4.0.0
- "AssemblyFileVersion" should be: `major.minor.patch.appVeyorBuildVersion`, eg. 4.2.2.1251 for NLog 4.2.2
- "BuildVersion" should be: `major.minor.patch` where `.patch` is ommited when 0. E.g 4.0, 4.1, 4.1.1, 4.2

Example of correct version numbers in NuGet Package explorer:

![image](https://cloud.githubusercontent.com/assets/5808377/11546997/fbfad58a-9950-11e5-952d-f7369f747089.png)


Pull request management
===

When reviewing a pull request, check the following:

- Ensure the pull request has a good, descriptive name.
- **Important:** set the Milestone.
- Add the applicable Labels.  
  Eg.
  - Type: `bug`, `enhancement`
  - Tests: `needs unittests`, `has unittests`
  - Status: `waiting for review`, `almost ready`, `ready for merge`
- Set the Assignee. It must indicate who is currently holding the ball.   
  For example, if you intend to review, assign to yourself. If, after the review, some changes need to be made, assign it back to the PR author.