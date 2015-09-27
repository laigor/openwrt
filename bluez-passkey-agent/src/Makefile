all: passkey-agent

passkey-agent: passkey-agent.c
	$(CC) $(CFLAGS) $(LDFLAGS) -o $@ $<

clean:
	rm -f passkey-agent
