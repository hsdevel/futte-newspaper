# qb-newspaper

This standalone resource will add a newspaper functionality to your beautiful QBCore FiveM server.

### Preview
| Opening newspaper | Reporter actions | Buying newspaper |
|--------------------| --------------- | -----------------|
| ![Opening newspaper](https://i.imgur.com/zEXI3oh.png) | ![Opening newspaper](https://i.imgur.com/68pjuKY.png) | ![Buying newspaper](https://i.imgur.com/ounIQJY.png) |

This resource is still in active development. Below features will be/have been implemented.

- [ ] Prison sentences
- [ ] City news (release notes for city)
- [ ] Action feedback
- [x] Live form validation
- [x] Image URL validation
- [x] Update stories
- [ ] Preview story before publishing
- [x] Input sanitization
- [ ] Hide news image if it returns 404 after request

Feel free to report bugs or improvements and they'll be looked at.

### Dependencies
- qb-target
- qb-inventory
- oxmysql

## Implementation

1. Navigate to ./web and run `npm install` to install all dependencies. If you don't already have node.js you can [download it here](https://nodejs.org/en/download/).'
2. Run `npm run dev` in ./web to compile the GUI. 
3. Add the newspaper.png image in the root of the resource into your qb-inventory folder, where all the other images are located.
4. Add following to your shared.lua file:

```lua
['newspaper'] = {['name'] = 'newspaper', ['label'] = 'Newspaper', ['weight'] = 10, ['type'] = 'item', ['image'] = 'newspaper.png', ['unique'] = false , ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Los Santos Newspaper'},
```

:bulb: When you are done working with the resource run `npm run build` to minify and uglify the resource to decrease the resource size.

## Configuration

There are quite a lot of configurations possible out-of-the-box with qb-newspaper. This consists of two files: `config.js` and `config.lua`.

**Config.js**
```javscript
export const Config = {
	newspaperTitle: 'QB-News',
	tabs: {
		showPrisonSentences: true,
		showCityNews: true,
	},
	articles: {
		showImage: true,
		showTitle: true,
		showDate: true,
		showPublisher: true,
		titleMaxLength: 60,
	},

	publishArticleControls: [
		['bold', 'italic', 'underline', 'strike'],
		['blockquote', 'image'],
		[{ list: 'ordered' }, { list: 'bullet' }],
	],
	reporter: [
		{
			grade: 0,
			canPublish: true,
			canEdit: true,
			canDelete: true,
		},
		{
			grade: 1,
			canPublish: true,
			canEdit: true,
			canDelete: true,
		},
		{
			grade: 2,
			canPublish: true,
			canEdit: true,
			canDelete: true,
		},
		{
			grade: 3,
			canPublish: true,
			canEdit: true,
			canDelete: true,
		},
	],
	text: {
		tabs: {
			newspaper: 'Newspaper',
			prisonSentences: 'Prison sentences (coming soon)',
			cityUpdates: 'City updates (coming soon)',
			reporterActions: 'Reporter actions',
		},
		prisonSentences: {},
		cityUpdates: {},
		reporterActions: {
			title: 'Reporter actions',
			noPermissions: 'You have no reporter permissions.',
			publishNewStory: 'Publish a new story',
			updateStories: 'Update stories',
			deleteStories: 'Delete stories',
			publishStory: {
				textareaPlaceholder: 'Article content..',
				imagePlaceholder: 'Image URL (Optional)',
				titlePlaceholder: 'Title (Required)',
				publish: 'Publish',
				update: 'Update',
				discardChanges: 'Discard changes',
				preview: 'Preview (Coming soon)',
				wrongImageFormat:
					'Wrong image format. Either .jpg, .jpeg, .png. .webp, .avif, .gif, or .svg expected',
				required: 'Required',
			},
		},
		articles: {
			writtenBy: 'Written by',
			on: 'on',
			latestStories: 'Latest stories',
		},
	},
};
```

**Config.lua**
```lua
Config.BuyNewspaperText = 'Buy newspaper' -- Text shown with qb-target
Config.BuyNewspaperIcon = 'fas fa-newspaper' -- Icon shown with qb-target
Config.Price = 100 -- Price of buying the newspaper
```

