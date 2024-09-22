<script lang="ts">
	import '../app.css';

	import Triangle from 'lucide-svelte/icons/triangle';
	import Bot from 'lucide-svelte/icons/bot';
	import SquareTerminal from 'lucide-svelte/icons/square-terminal';
	import CodeXML from 'lucide-svelte/icons/code-xml';
	import Settings2 from 'lucide-svelte/icons/settings-2';
	import LifeBuoy from 'lucide-svelte/icons/life-buoy';
	import Book from 'lucide-svelte/icons/book';
	import SquareUser from 'lucide-svelte/icons/square-user';

	import { Button } from '$lib/components/ui/button/index.js';
	import * as Tooltip from '$lib/components/ui/tooltip/index.js';
	import * as Card from '$lib/components/ui/card/index.js';
	import * as DropdownMenu from '$lib/components/ui/dropdown-menu';
	import { ChevronRight, CircleX, Trash2 } from 'lucide-svelte';


	let logs = [
		{
			time: '10:00',
			message: 'Card Content'
		},
		{
			time: '10:00',
			message: 'Card Content'
		},
		{
			time: '10:00',
			message: 'Card Content'
		}
	]
</script>

<div class="flex flex-col h-screen w-full">
	<div class="grid flex-1 w-full pl-[53px] relative">
		<aside class="inset-y fixed left-0 z-20 flex h-full pb-[25px] flex-col border-r">
			<div class="border-b p-2">
				<Button variant="outline" size="icon" aria-label="Home">
					<Triangle class="size-5 fill-foreground" />
				</Button>
			</div>
			<nav class="grid gap-1 p-2">
				<Tooltip.Root>
					<Tooltip.Trigger asChild let:builder>
						<Button
							variant="ghost"
							size="icon"
							class="rounded-lg bg-muted"
							aria-label="Playground"
							builders={[builder]}
						>
							<SquareTerminal class="size-5" />
						</Button>
					</Tooltip.Trigger>
					<Tooltip.Content side="right" sideOffset={5}>Playground</Tooltip.Content>
				</Tooltip.Root>
				<Tooltip.Root>
					<Tooltip.Trigger asChild let:builder>
						<Button
							variant="ghost"
							size="icon"
							class="rounded-lg"
							aria-label="Models"
							builders={[builder]}
						>
							<Bot class="size-5" />
						</Button>
					</Tooltip.Trigger>
					<Tooltip.Content side="right" sideOffset={5}>Models</Tooltip.Content>
				</Tooltip.Root>
				<Tooltip.Root>
					<Tooltip.Trigger asChild let:builder>
						<Button
							variant="ghost"
							size="icon"
							class="rounded-lg"
							aria-label="API"
							builders={[builder]}
						>
							<CodeXML class="size-5" />
						</Button>
					</Tooltip.Trigger>
					<Tooltip.Content side="right" sideOffset={5}>API</Tooltip.Content>
				</Tooltip.Root>
				<Tooltip.Root>
					<Tooltip.Trigger asChild let:builder>
						<Button
							variant="ghost"
							size="icon"
							class="rounded-lg"
							aria-label="Documentation"
							builders={[builder]}
						>
							<Book class="size-5" />
						</Button>
					</Tooltip.Trigger>
					<Tooltip.Content side="right" sideOffset={5}>Documentation</Tooltip.Content>
				</Tooltip.Root>
				<Tooltip.Root>
					<Tooltip.Trigger asChild let:builder>
						<Button
							variant="ghost"
							size="icon"
							class="rounded-lg"
							aria-label="Settings"
							builders={[builder]}
						>
							<Settings2 class="size-5" />
						</Button>
					</Tooltip.Trigger>
					<Tooltip.Content side="right" sideOffset={5}>Settings</Tooltip.Content>
				</Tooltip.Root>
			</nav>
			<nav class="mt-auto grid gap-1 p-2">
				<Tooltip.Root>
					<Tooltip.Trigger asChild let:builder>
						<Button
							variant="ghost"
							size="icon"
							class="mt-auto rounded-lg"
							aria-label="Help"
							builders={[builder]}
						>
							<LifeBuoy class="size-5" />
						</Button>
					</Tooltip.Trigger>
					<Tooltip.Content side="right" sideOffset={5}>Help</Tooltip.Content>
				</Tooltip.Root>
				<Tooltip.Root>
					<Tooltip.Trigger asChild let:builder>
						<Button
							variant="ghost"
							size="icon"
							class="mt-auto rounded-lg"
							aria-label="Account"
							builders={[builder]}
						>
							<SquareUser class="size-5" />
						</Button>
					</Tooltip.Trigger>
					<Tooltip.Content side="right" sideOffset={5}>Account</Tooltip.Content>
				</Tooltip.Root>
			</nav>
		</aside>
		<div class="flex flex-col relative">
			<slot></slot>

			<div class="w-full p-3 pr-[65px] bottom-[25px] fixed flex flex-col overflow-hidden">
				<Card.Root class="h-[300px] flex flex-col">
				  <Card.Header class="border-b py-2">
					<div class="flex flex-row justify-between">
						<div class="flex flex-col">
							<Card.Title>Logs</Card.Title>
							<Card.Description>List of logs operations from the backend</Card.Description>
						</div>
						<DropdownMenu.Root>
							<DropdownMenu.Trigger>Open</DropdownMenu.Trigger>
							<DropdownMenu.Content>
							  <DropdownMenu.Group>
								<DropdownMenu.Label>Console</DropdownMenu.Label>
								<DropdownMenu.Separator />
								<DropdownMenu.Item class="flex space-x-2"> <Trash2 class="size-5" /> <span>Clear</span></DropdownMenu.Item>
								<DropdownMenu.Item class="flex space-x-2"><CircleX class="size-5"/> <span>Close</span></DropdownMenu.Item>
							  </DropdownMenu.Group>
							</DropdownMenu.Content>
						  </DropdownMenu.Root>
					</div>
				  </Card.Header>
				  <Card.Content class="flex-1 overflow-y-auto">
					{#each logs as log}
					<div class="hover:border-b py-1 flex space-x-2 items-center font-light text-sm">
						<ChevronRight class="size-3"/>
						<span>{log.message}</span>
					</div>
					{/each}
				  </Card.Content>
				  <Card.Footer class="border-t py-2">
					<p>{logs.length} log{logs.length === 1 ? '' : 's'}</p>
				  </Card.Footer>
				</Card.Root>
			</div>
		</div>
	</div>

	<footer class="flex h-[25px] z-20 border-t bg-background px-4 fixed bottom-0 w-full"></footer>
</div>
