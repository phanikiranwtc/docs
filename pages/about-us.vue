<template>
    <div>
        <Head>
            <Title>About Us</Title>
            <Meta name="description"
                  content="Discover the team and values behind our mission to empower data-driven organizations worldwide"/>
        </Head>

        <CompanyHeader/>
        <CompanyOrchestration/>
        <CompanyPlatform/>
        <CompanyLaunch/>
        <CompanyValue/>
        <CompanyTeam/>
        <CompanyPress/>
        <LayoutFooterContact
            title="Join Our Team and Contribute to the Future of Data Orchestration"
            purpleButtonText="See open roles"
            purpleButtonHref="/careers"
        />
    </div>
</template>

<script setup>
    const { origin } = useRequestURL()
    useHead({
        meta: [
            { name: 'twitter:card', content: 'summary_large_image' },
            { name: 'twitter:site', content: '@kestra_io' },
            { name: 'twitter:title', content: "about-us" },
            {
                name: 'twitter:description',
                content: "Discover the team and values behind our mission to empower data-driven organizations worldwide"
            },
            { name: 'twitter:image', content: `${origin}/landing/company/header.svg` },
            { name: 'twitter:image:alt', content: "About-Us" }
        ]
    })

</script>
