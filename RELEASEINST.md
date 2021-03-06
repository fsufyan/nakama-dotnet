Release Instructions
===

These instructions guide the release process for new official Nakama client SDK build and releases to [Nuget](https://www.nuget.org/packages/NakamaClient/).

## Steps

1. Update and tidy up the CHANGELOG.

2. Run the test suite for the codebase. See the README for steps.

3. Create the release commit and tag it.

   ```shell
   git add CHANGELOG
   git commit -m "Nakama .NET 2.5.0 release."
   git tag -a v2.5.0 -m "v2.5.0"
   git push origin v2.5.0 master
   ```

4. Create a release build of the code.

   ```shell
   dotnet build -c Release /p:AssemblyVersion=2.5.0.0 src/Nakama/Nakama.csproj
   ```

5. Create a release on GitHub: https://github.com/heroiclabs/nakama-dotnet/releases/new

6. Copy the CHANGELOG section to the release notes. Upload the release DLL to be part of the GitHub release. Publish it.

7. Package and push the release to Nuget.

   ```shell
   dotnet pack -p:AssemblyVersion=2.5.0.0 -p:PackageVersion=2.5.0 -c Release src/Nakama/Nakama.csproj
   dotnet nuget push ./src/Nakama/bin/Release/NakamaClient.2.5.0.nupkg -k "somekey" -s https://api.nuget.org/v3/index.json
   ```

8. Update CHANGELOG with section for new unreleased changes.

   ```shell
   git add CHANGELOG.md
   git commit -m "Set new development version."
   git push origin master
   ```
