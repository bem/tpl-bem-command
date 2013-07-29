BIN = ./node_modules/.bin

.PHONY: all
all:

lib-cov: clean-coverage
	$(BIN)/istanbul instrument --output lib-cov --no-compact --variable global.__coverage__ lib

.PHONY: test
test:
	$(BIN)/mocha

.PHONY: coverage
coverage: lib-cov
	{APP_ENV}_COVER=1 ISTANBUL_REPORTERS=lcovonly,text-summary,html $(BIN)/mocha --reporter mocha-istanbul
	-cat lcov.info | $(BIN)/coveralls
	@echo
	@echo Open html-report/index.html file in your browser

.PHONY: clean
clean: clean-coverage

.PHONY: clean-coverage
clean-coverage:
	-rm -rf lib-cov
	-rm -rf html-report
