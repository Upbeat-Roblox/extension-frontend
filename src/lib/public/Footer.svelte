<script lang="ts">
    import {
        aboutLinks,
        supportLinks,
        socialLinks,
        type link,
        type socialLink,
    } from "./navigationLinks";
</script>

<footer class="flex-center flex-center mt-20 flex-col gap-7 px-10 py-16 md:px-[10%]">
    <div class="flex w-full flex-col gap-16 md:flex-row md:gap-20 lg:gap-28">
        <div class="w-full flex-shrink-0 md:w-[35%]">
            <div>
                <p class="text-3xl font-bold">Upbeat</p>
                <p class="text-light">Copyright © 2024 Upbeat. All rights reserved.</p>
            </div>

            <p class="text-dark mt-5 text-sm">
                Upbeat is an independent product and is not affiliated with, endorsed by, or
                associated with Roblox Corporation. All Roblox logos and trademarks are the property
                of Roblox Corporation. Upbeat is designed to modify aspects of the Roblox website
                only, without altering or interacting with any in-game features on the Roblox
                platform.
            </p>
        </div>

        <div
            class="grid w-full grid-cols-1 grid-rows-1 gap-10 md:flex-grow md:grid-cols-3 md:grid-rows-1"
        >
            {#snippet navigationLink(text: string, url: string)}
                <a class="text-light select-none" href={url}>{text}</a>
            {/snippet}

            {#snippet navigationSocialLink(text: string, icon: string, url: string)}
                <a class="text-light flex select-none items-center gap-1.5" href={url}>
                    <img class="aspect-square h-5 dark:invert" src={icon} alt={url} />
                    {text}
                </a>
            {/snippet}

            {#snippet list(title: string, entries: link[] | socialLink[])}
                <div class="flex flex-col gap-1.5 md:pt-2.5">
                    <p class="text-dark mb-1 text-sm font-semibold">
                        {title}
                    </p>

                    {#each entries as entry}
                        {#if "icon" in entries[0]}
                            {@render navigationSocialLink(
                                entry.text,
                                (entry as socialLink).icon,
                                entry.url
                            )}
                        {:else}
                            {@render navigationLink(entry.text, entry.url)}
                        {/if}
                    {/each}
                </div>
            {/snippet}

            {@render list("Product", aboutLinks)}
            {@render list("Support", supportLinks)}
            {@render list("Where to find us", socialLinks)}
        </div>
    </div>

    <div class="divider-x w-full"></div>

    <p class="text-dark">Developed as a hobby project by Landon Redmond</p>
</footer>
