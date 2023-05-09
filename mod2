    // updated for 1.13.1
    void unlock()
    {
    	// set up a pattern scan for these two
    	uintptr_t cleanup_instr = base + 0x27E10C2; // 0F 84 ? ? ? ? 83 78 04 00 0F 86 [resolve jz then add 2]
    	uintptr_t to_swap = base + 0xBBF3460; // 48 89 05 ? ? ? ? 48 89 3D ? ? ? ? 8D 57 01 E8 [resolve mov]
     
    	char shell[] = { 0x48, 0x83, 0xC4, 0x08, 0x48, 0xB8, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xE9, 0x00, 0x00, 0x00, 0x00, 0x01 };
    	*(__int64*)(shell + 6) = to_swap - 0x87;
    	*(int*)(shell + 15) = cleanup_instr - to_swap + 0x83;
    	memcpy((void*)(to_swap - 0x96), shell, 20);
     
    	*(__int64*)(to_swap + 8) = to_swap - 0x96;
    	*(__int64*)to_swap = to_swap;
    }
