##### Firmware:
Programa instalado em um chip on-board que roda **antes do sistema operacional**.

---

**BIOS** = _Basic Input/Output System_  
- Criado nos **anos 80**.  
- É o **primeiro código** que roda quando você liga o computador.  
- **Funções principais:**  
    - Iniciar o hardware básico (CPU, memória, teclado, disco).  
    - Procurar um dispositivo de boot (HD, pendrive, CD).  
    - Passar o controle para o sistema operacional.  
- Trabalha em **modo 16 bits** (bem limitado).  
- Interface simples (aquela telinha azul antiga).  
- Usa o particionamento **MBR (Master Boot Record)**:  
    - Máx. **2 TB por disco**  
    - Até **4 partições primárias**

> [!note]  
> 📦 **Como funciona o MBR (Master Boot Record):**  
> - BIOS lê os **primeiros 512 bytes** do disco de boot.  
> - **446 bytes** → bootloader.  
> - **64 bytes** → tabela de partições.  
> - **2 bytes finais** → assinatura `55 AA`.  
>   
> 💡 Bootloader do MBR é mínimo, quase sempre chama um **segundo estágio** (ex: GRUB ou Windows Boot Manager).

---

**UEFI** = _Unified Extensible Firmware Interface_  
- Criado nos **anos 2000** para substituir o BIOS.  
- É o **firmware moderno** que roda antes do sistema operacional.  
- **Funções principais:**  
    - Inicializa o hardware de forma mais avançada.  
    - Permite **menus gráficos**, suporte a **mouse**, **rede** e **drivers**.  
    - Suporta **Secure Boot** (o SO só inicializa se for assinado digitalmente).  
- Trabalha em **modo 32/64 bits** (muito mais poderoso).  
- Usa o particionamento **GPT (GUID Partition Table):**  
    - Discos de até **9,4 zettabytes** (praticamente infinito).  
    - Até **128 partições** por disco.

> [!note]  
> 📦 **Como funciona o GPT (GUID Partition Table):**  
> - Mantém **cópias redundantes** da tabela de partições (mais seguro que MBR).  
> - Cada partição tem um **GUID único**.  
> - Usa **checksums (CRC32)** para detectar corrupção.  
> - Muito mais confiável que o MBR, que só possuía uma tabela simples.

---

### 🔄 Comparação: BIOS vs UEFI

| Característica  | **BIOS** | **UEFI** |
|-----------------|----------|----------|
| Ano de criação  | Anos 80  | Anos 2000 |
| Modo de operação| 16 bits  | 32/64 bits |
| Particionamento | MBR (2 TB, 4 partições) | GPT (9,4 ZB, 128 partições) |
| Interface       | Texto simples (azul) | Gráfica, mouse, drivers |
| Segurança       | Sem verificação | Secure Boot |
