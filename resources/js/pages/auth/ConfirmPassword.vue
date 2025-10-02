<script setup lang="ts">
import InputError from '@/components/InputError.vue';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import AuthLayout from '@/layouts/AuthLayout.vue';
import { Form, Head } from '@inertiajs/vue3';
import { LoaderCircle } from 'lucide-vue-next';

import { useI18n } from 'vue-i18n';
const { t } = useI18n();
</script>

<template>
    <AuthLayout :title="t('Confirm your password')" :description="t('This is a secure area of the application. Please confirm your password before continuing.')">
        <Head :title="t('Confirm password')" />

        <Form method="post" :action="route('password.confirm')" reset-on-success v-slot="{ errors, processing }">
            <div class="space-y-6">
                <div class="grid gap-2">
                    <Label htmlFor="password">{{ t('Password') }}</Label>
                    <Input
                        id="password"
                        type="password"
                        name="password"
                        class="block w-full mt-1"
                        required
                        autocomplete="current-password"
                        autofocus
                    />

                    <InputError :message="errors.password" />
                </div>

                <div class="flex items-center">
                    <Button class="w-full" :disabled="processing">
                        <LoaderCircle v-if="processing" class="w-4 h-4 animate-spin" />
                        {{ t('Confirm Password') }}
                    </Button>
                </div>
            </div>
        </Form>
    </AuthLayout>
</template>
