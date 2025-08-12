# Changesets Guide for NextBlock GitHub Organization

This repository uses [Changesets](https://github.com/changesets/changesets) to manage versioning and changelogs for the NextBlock GitHub organization documentation and policies.

## What are Changesets?

Changesets are a way to track changes to your repository that should result in a new version being published. They help maintain a clear changelog and automate the release process.

## How to Use Changesets

### 1. Creating a Changeset

When you make changes that should be versioned (like updating policies, documentation, or organization information), create a changeset:

```bash
npm run changeset
```

This will prompt you to:
- Select the type of change (major, minor, patch)
- Write a description of the changes
- Select which packages are affected

### 2. Types of Changes

- **Major**: Breaking changes (e.g., major policy updates, structural changes)
- **Minor**: New features or significant updates (e.g., new policies, updated documentation)
- **Patch**: Bug fixes or minor updates (e.g., typo fixes, small clarifications)

### 3. Workflow

1. Make your changes to the repository
2. Create a changeset: `npm run changeset`
3. Commit your changes and the changeset file
4. Push to create a pull request
5. The GitHub Action will automatically create a release PR when changesets are present
6. Review and merge the release PR to publish the new version

### 4. Available Scripts

- `npm run changeset` - Create a new changeset
- `npm run version` - Version packages based on changesets
- `npm run release` - Publish packages (if applicable)

## GitHub Actions

This repository includes two automated workflows:

1. **Create Changeset** (`.github/workflows/changeset.yml`)
   - Runs on pull requests to main
   - Helps create changesets for contributors

2. **Release** (`.github/workflows/release.yml`)
   - Runs on pushes to main
   - Automatically creates release pull requests when changesets are present
   - Publishes new versions when release PRs are merged

## Configuration

The changesets configuration is in `.changeset/config.json`:

- **changelog**: Uses the default changelog generator
- **commit**: Disabled (we handle commits manually)
- **access**: Restricted (appropriate for organization repositories)
- **baseBranch**: Main branch
- **updateInternalDependencies**: Patch level updates

## Best Practices

1. **Always create a changeset** for meaningful changes
2. **Be descriptive** in your changeset messages
3. **Use appropriate change types** (major/minor/patch)
4. **Review release PRs** before merging
5. **Keep changesets focused** on a single logical change

## Examples

### Policy Update
```bash
npm run changeset
# Select: minor
# Description: "Updated privacy policy to reflect new data handling practices"
```

### Documentation Fix
```bash
npm run changeset
# Select: patch
# Description: "Fixed typos in README and updated contact information"
```

### Major Organizational Change
```bash
npm run changeset
# Select: major
# Description: "Restructured organization policies and updated terms of service"
```

## Need Help?

- [Changesets Documentation](https://github.com/changesets/changesets)
- [Common Questions](https://github.com/changesets/changesets/blob/main/docs/common-questions.md)
- Contact the NextBlock team for repository-specific questions
